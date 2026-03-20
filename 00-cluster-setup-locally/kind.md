# 🐳 Environment Setup — kind (Kubernetes IN Docker)

kind runs Kubernetes clusters inside Docker containers.
It's faster to spin up and supports multi-node clusters — great for Phase 3 questions (kubeadm, worker nodes, cluster upgrades).

---

## Prerequisites

```bash
# Docker must be running
docker --version
```

---

## Install kind

### macOS
```bash
brew install kind
```

### Linux
```bash
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.23.0/kind-linux-amd64
chmod +x ./kind && sudo mv ./kind /usr/local/bin/kind
```

### Windows
```powershell
winget install kind
```

---

## Single Node Cluster (Phase 1 & 2 Questions)

```bash
kind create cluster --name cka-practice
kubectl cluster-info --context kind-cka-practice
kubectl get nodes
```

---

## Multi-Node Cluster (Phase 3 Questions)

Create a config file first:

```yaml
# kind-multinode.yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: worker
- role: worker
```

```bash
kind create cluster --name cka-multi --config kind-multinode.yaml
kubectl get nodes
# NAME                      STATUS   ROLES
# cka-multi-control-plane   Ready    control-plane
# cka-multi-worker          Ready    <none>
# cka-multi-worker2         Ready    <none>
```

---

## Useful Commands

```bash
kind get clusters                        # list all kind clusters
kind delete cluster --name cka-practice  # delete a cluster
kind load docker-image nginx:1.25.3 --name cka-practice  # load image into cluster
```

---

## minikube vs kind — Which Should You Use?

| | minikube | kind |
|--|----------|------|
| Setup speed | Slower | Fast |
| Multi-node | ❌ (single node) | ✅ |
| SSH into node | ✅ `minikube ssh` | ✅ `docker exec` |
| Best for | Phase 1–2 | Phase 3 (cluster admin) |
| Ingress addon | ✅ built-in | Needs extra config |

**Recommendation:** Use minikube for Phases 1 and 2. Switch to kind for Phase 3 cluster administration questions.

---

→ [Set up minikube instead](./minikube.md) · [Set up aliases](./aliases.md)
