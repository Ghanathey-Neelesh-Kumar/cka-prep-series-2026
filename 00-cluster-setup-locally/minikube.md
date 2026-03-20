# 🖥️ Environment Setup — minikube

minikube runs a full Kubernetes cluster locally on your machine.
It's the recommended environment for practising all questions in this series.

---

## Install minikube

### macOS
```bash
brew install minikube
```

### Linux
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
```

### Windows
```powershell
winget install minikube
```

---

## Install kubectl

### macOS
```bash
brew install kubectl
```

### Linux
```bash
curl -LO "https://dl.k8s.io/release/$(curl -sL https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install kubectl /usr/local/bin/kubectl && rm kubectl
```

### Windows
```powershell
winget install kubectl
```

---

## Start Your Cluster

```bash
minikube start --cpus=2 --memory=4096 --kubernetes-version=v1.31.0
```

Verify:
```bash
kubectl get nodes
# NAME       STATUS   ROLES           AGE   VERSION
# minikube   Ready    control-plane   1m    v1.31.0
```

---

## Enable Required Addons

```bash
minikube addons enable ingress        # needed for Ingress questions
minikube addons enable metrics-server # needed for resource/top questions
```

---

## Useful Commands

```bash
minikube status       # check cluster health
minikube stop         # pause the cluster
minikube start        # resume
minikube delete       # wipe and start fresh
minikube ssh          # SSH into the node (Phase 3 questions)
minikube ip           # get the cluster IP
```

---

## Smoke Test — Verify Everything Works

```bash
kubectl run smoke --image=nginx:1.25.3 --restart=Never
kubectl get pod smoke
# STATUS: Running ✅
kubectl delete pod smoke
```

---

→ [Set up aliases](./aliases.md) · [Try kind instead](./kind.md)
