# 🧠 Exam Tips

---

## The First 60 Seconds — Run These Before Any Question

```bash
alias k=kubectl
source <(kubectl completion bash)
complete -F __start_kubectl k
kubectl config get-contexts
```

These cost you 60 seconds once and save you 10+ minutes over 2 hours.

---

## Read All Questions First (5 Minutes)

Before solving anything, scan every question:
- Note the weight % next to each question
- Tag the easy ones — do them first
- Flag the hard ones — skip them for now

**Prioritise:** high-weight + easy first. Save hard questions for the end.

---

## The Question Checklist — Do This for Every Task

```
✅ Read the question twice
✅ Note the namespace
✅ Switch context: kubectl config use-context <context>
✅ Solve
✅ Verify: kubectl get <resource>
✅ Move on
```

Never skip the context switch. Never skip the verify.

---

## Imperative Commands Save Minutes

```bash
# Faster than writing YAML from scratch
k create deployment web --image=nginx
k expose deployment web --port=80
k create role reader --verb=get,list --resource=pods -n dev
k create rolebinding rb --role=reader --user=jane -n dev
```

Use YAML only when the resource needs complex spec (volumes, probes, affinity).

---

## The `--dry-run=client -o yaml` Power Move

```bash
# Generate YAML scaffold in 5 seconds
k run mypod --image=nginx --dry-run=client -o yaml > pod.yaml
# Edit pod.yaml to add the complex bits
k apply -f pod.yaml
```

---

## Kubernetes Docs — What to Actually Look Up

| Task | URL path on kubernetes.io |
|------|---------------------------|
| kubectl reference | `/docs/reference/kubectl/cheatsheet/` |
| etcd backup | `/docs/tasks/administer-cluster/configure-upgrade-etcd/` |
| Cluster upgrade | `/docs/tasks/administer-cluster/kubeadm/kubeadm-upgrade/` |
| RBAC | `/docs/reference/access-authn-authz/rbac/` |
| NetworkPolicy | `/docs/concepts/services-networking/network-policies/` |
| PV & PVC | `/docs/concepts/storage/persistent-volumes/` |

Use `Ctrl+F` on any docs page. Don't read — scan for the code example you need.

---

## Passing Score is 66% — Use It Strategically

You don't need to be perfect. You need 66%.

- You can skip 2–3 hard questions and still pass if you ace the rest
- Partial solutions sometimes earn partial marks
- A working messy solution scores the same as an elegant one
