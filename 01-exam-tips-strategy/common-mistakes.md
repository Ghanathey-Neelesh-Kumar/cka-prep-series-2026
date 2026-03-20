# 💀 Common Mistakes
> Real mistakes. Real mark deductions. Don't repeat them.

---

## Mistake 1 — Forgetting to Switch Context

**What happens:** You complete the task perfectly. On the wrong cluster.
Score: zero.

```bash
# ALWAYS run this before starting any question
kubectl config use-context <context-from-question>

# Verify you're on the right cluster
kubectl config current-context
```

**Drill this until it's the first thing you type. Every. Single. Question.**

---

## Mistake 2 — Not Verifying Your Work

**What happens:** You apply the fix, move on, don't check. The pod crashes again 30 seconds later. You've already moved to the next question.

```bash
# After every fix — always verify
kubectl get pod <n> -n <ns>
kubectl rollout status deployment/<n> -n <ns>
kubectl get endpoints <svc> -n <ns>
```

One minute of verification saves five minutes of confusion.

---

## Mistake 3 — Stopping After the First Bug

**What happens:** You find one issue, fix it, mark the question done. There were three bugs. You score partial or zero.

**Rule:** After fixing one bug, re-read the entire manifest. Scan all fields.
Common multi-bug combinations:
- Bad image tag + wrong probe port
- Resource limit < request + wrong probe path
- Wrong selector label + wrong target port

---

## Mistake 4 — Editing a Running Pod Spec Directly

**What happens:** You try `kubectl edit pod <n>` to change an immutable field (image, volumes, etc). Kubernetes rejects the save.

```bash
# Correct approach for pods:
kubectl get pod <n> -o yaml > pod.yaml
# Edit pod.yaml
kubectl delete pod <n> --force --grace-period=0
kubectl apply -f pod.yaml
```

For Deployments, `kubectl edit deployment <n>` works fine — Deployments are mutable.

---

## Mistake 5 — Service Selector Doesn't Match Pod Labels

**Symptom:** Service exists, pod is running, but `kubectl get endpoints <svc>` shows `<none>`.

```bash
# Check the service selector
kubectl describe svc <n> | grep Selector

# Check the pod labels
kubectl get pod <n> --show-labels

# They must match exactly — key AND value
```

This is the single most common networking bug in the exam.

---

## Mistake 6 — Wrong Namespace

**What happens:** You create the resource in `default` instead of the namespace specified in the question.

```bash
# Always check the question for namespace
# Always add -n <namespace> to every command
# Or set a default namespace for the session:
kubectl config set-context --current --namespace=<ns>
```

---

## Mistake 7 — Using `--previous` Too Late

**What happens:** The container has already been restarted 4 times. You run `kubectl logs <pod>` and see empty output. You think there are no logs. There are — they're in the previous run.

```bash
kubectl logs <pod> -n <ns> --previous    # always try this if logs are empty
```

---

## Mistake 8 — Resource Limit Less Than Request

**What happens:** Kubernetes silently rejects the pod. You see an error in `describe` but miss it.

```bash
# Always: limits >= requests
resources:
  requests:
    memory: "64Mi"
  limits:
    memory: "128Mi"   # never lower than requests
```

---

## Mistake 9 — Not Using `--dry-run=client -o yaml`

**What happens:** You spend 3 minutes writing YAML from scratch for a simple deployment.

```bash
# Generate it in 5 seconds, then edit
kubectl create deployment my-dep --image=nginx --dry-run=client -o yaml > dep.yaml
kubectl apply -f dep.yaml
```

---

## Mistake 10 — Spending Too Long on One Question

**What happens:** One hard question eats 20 minutes. You run out of time on 3 easier questions that were worth more marks combined.

**Rule:** Hard cap at 10 minutes per question. Flag it. Move on. Return at the end.
A 66% pass rate means you can leave marks on the table and still pass.
