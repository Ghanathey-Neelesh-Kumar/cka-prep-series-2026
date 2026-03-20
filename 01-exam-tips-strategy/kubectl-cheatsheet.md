# ⚡ kubectl Cheatsheet
> Run this first, every session: `alias k=kubectl && source <(kubectl completion bash) && complete -F __start_kubectl k`

---

## Get & Inspect

```bash
k get pods -n <ns>                        # pods in namespace
k get pods -A                             # all namespaces
k get pods -o wide                        # node + IP
k get pods -w                             # watch live
k get all -n <ns>                         # all resource types
k describe pod <n> -n <ns>               # full detail + events ← use this constantly
k get pod <n> -o yaml > pod.yaml         # dump to file for editing
k explain pod.spec.containers            # field documentation
```

---

## Create (Imperative — Fastest in Exam)

```bash
k run <n> --image=nginx:1.25.3                                    # pod
k run <n> --image=nginx --dry-run=client -o yaml > pod.yaml      # generate YAML

k create deployment <n> --image=nginx --replicas=3               # deployment
k create deployment <n> --image=nginx --dry-run=client -o yaml   # generate YAML

k expose pod <pod> --port=80 --name=<svc>                        # clusterip svc from pod
k expose deployment <dep> --port=80 --type=NodePort              # nodeport svc

k create configmap <n> --from-literal=key=value
k create secret generic <n> --from-literal=password=secret
k create namespace <n>
k create serviceaccount <n> -n <ns>

k create role <n> --verb=get,list,watch --resource=pods -n <ns>
k create rolebinding <n> --role=<role> --user=<user> -n <ns>
k create rolebinding <n> --role=<role> --serviceaccount=<ns>:<sa> -n <ns>
k create clusterrole <n> --verb=get,list --resource=pods
k create clusterrolebinding <n> --clusterrole=<role> --user=<user>
```

---

## Edit & Update

```bash
k edit deployment <n>
k scale deployment <n> --replicas=5
k set image deployment/<n> <container>=nginx:1.26
k rollout status deployment/<n>
k rollout undo deployment/<n>
k rollout undo deployment/<n> --to-revision=2
k rollout history deployment/<n>
```

---

## Delete

```bash
k delete pod <n>
k delete pod <n> --force --grace-period=0    # force — saves time in exam
k delete -f manifest.yaml
k delete namespace <n>                        # deletes everything inside
```

---

## Troubleshoot

```bash
k logs <pod> -n <ns>
k logs <pod> -n <ns> --previous             # crashed container — use this
k logs <pod> -n <ns> -c <container>         # specific container
k exec -it <pod> -n <ns> -- bash
k exec -it <pod> -n <ns> -- sh

k get events -n <ns> --sort-by='.lastTimestamp'
k get events -A --sort-by='.lastTimestamp'

k top nodes
k top pods -n <ns>
```

---

## Networking

```bash
k port-forward pod/<pod> 8080:80 -n <ns>
k port-forward svc/<svc> 8080:80 -n <ns>
k get endpoints <svc> -n <ns>              # no endpoints = selector mismatch

# Debug pod
k run debug --image=busybox --rm -it --restart=Never -- sh
k run debug --image=nicolaka/netshoot --rm -it --restart=Never -- bash

# DNS test
k exec -it <pod> -- nslookup <svc>.<ns>.svc.cluster.local
```

---

## RBAC Verification

```bash
k auth can-i get pods --as=<user> -n <ns>
k auth can-i --list --as=<user> -n <ns>
k auth can-i get secrets --as=system:serviceaccount:<ns>:<sa> -n <ns>
```

---

## Labels & Taints

```bash
k label node <n> disktype=ssd
k label node <n> disktype-                   # remove label
k taint node <n> key=value:NoSchedule
k taint node <n> key=value:NoSchedule-       # remove taint
```

---

## Contexts

```bash
k config get-contexts
k config use-context <n>
k config set-context --current --namespace=<ns>
```

---

## Speed Tricks

```bash
# Generate YAML without applying
k run nginx --image=nginx --dry-run=client -o yaml
k create deployment web --image=nginx --dry-run=client -o yaml

# Explain any field
k explain pod.spec.containers.resources.limits

# Force delete
k delete pod <n> --force --grace-period=0
```
