# 📄 YAML Templates
> Copy-paste ready. Edit the fields marked with `<angle brackets>`.
> On exam day: generate with `--dry-run=client -o yaml` and edit — faster than copying.

---

## Pod

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: <name>
  namespace: <namespace>
  labels:
    app: <name>
spec:
  containers:
  - name: <name>
    image: <image>:<tag>
    ports:
    - containerPort: <port>
    resources:
      requests:
        memory: "64Mi"
        cpu: "250m"
      limits:
        memory: "128Mi"
        cpu: "500m"
```

---

## Deployment

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: <name>
  namespace: <namespace>
spec:
  replicas: 3
  selector:
    matchLabels:
      app: <name>
  template:
    metadata:
      labels:
        app: <name>
    spec:
      containers:
      - name: <name>
        image: <image>:<tag>
        ports:
        - containerPort: <port>
```

---

## Service — ClusterIP

```yaml
apiVersion: v1
kind: Service
metadata:
  name: <name>
  namespace: <namespace>
spec:
  type: ClusterIP
  selector:
    app: <name>          # must match pod labels
  ports:
  - port: 80
    targetPort: <container-port>
```

---

## Service — NodePort

```yaml
apiVersion: v1
kind: Service
metadata:
  name: <name>
spec:
  type: NodePort
  selector:
    app: <name>
  ports:
  - port: 80
    targetPort: <container-port>
    nodePort: 30080      # 30000-32767 range
```

---

## ConfigMap

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: <name>
  namespace: <namespace>
data:
  APP_ENV: production
  LOG_LEVEL: info
```

---

## Secret

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: <name>
  namespace: <namespace>
type: Opaque
data:
  password: <base64-encoded-value>    # echo -n 'mysecret' | base64
```

---

## PersistentVolume

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: <name>
spec:
  capacity:
    storage: 1Gi
  accessModes:
  - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain
  hostPath:
    path: /data/<name>
```

---

## PersistentVolumeClaim

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: <name>
  namespace: <namespace>
spec:
  accessModes:
  - ReadWriteOnce
  resources:
    requests:
      storage: 500Mi
  storageClassName: ""    # "" = bind to static PV
```

---

## RBAC — Role + RoleBinding

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  name: <name>
  namespace: <namespace>
rules:
- apiGroups: [""]
  resources: ["pods"]
  verbs: ["get", "list", "watch"]
---
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: <name>
  namespace: <namespace>
subjects:
- kind: User
  name: <username>
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: Role
  name: <role-name>
  apiGroup: rbac.authorization.k8s.io
```

---

## NetworkPolicy — Allow Specific Traffic

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: <name>
  namespace: <namespace>
spec:
  podSelector:
    matchLabels:
      app: <target-app>
  policyTypes:
  - Ingress
  ingress:
  - from:
    - podSelector:
        matchLabels:
          app: <source-app>
    ports:
    - protocol: TCP
      port: <port>
```

---

## Ingress

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: <name>
  namespace: <namespace>
spec:
  ingressClassName: nginx
  rules:
  - host: <hostname>
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: <svc-name>
            port:
              number: 80
```

---

## Pod with Volume Mount

```yaml
spec:
  containers:
  - name: app
    image: nginx
    volumeMounts:
    - name: data
      mountPath: /data
  volumes:
  - name: data
    persistentVolumeClaim:
      claimName: <pvc-name>
```

---

## Readiness & Liveness Probes

```yaml
readinessProbe:
  httpGet:
    path: /
    port: 80
  initialDelaySeconds: 5
  periodSeconds: 10

livenessProbe:
  httpGet:
    path: /healthz
    port: 8080
  initialDelaySeconds: 10
  periodSeconds: 5
  failureThreshold: 3
```
