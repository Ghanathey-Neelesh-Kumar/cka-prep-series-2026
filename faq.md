# ❓ FAQ

Answers to everything you've been Googling.

---

**Q: Do I need to memorise YAML syntax?**
No. Use `kubectl <command> --dry-run=client -o yaml` to generate any resource.
Use `kubectl explain <resource>.<field>` to look up any field.
You only need to know the structure — not memorise every line.

---

**Q: How long should I study before attempting the exam?**
Most candidates need 6–10 weeks of consistent hands-on practice.
Theory alone is not enough. You must type commands daily.

---

**Q: Can I use the Kubernetes docs during the exam?**
Yes — one tab on `kubernetes.io` is allowed.
Pre-bookmark the etcd backup page, RBAC page, and kubectl cheatsheet.
Don't rely on docs for basics — you won't have time to read.

---

**Q: What's the hardest part of the exam?**
Time pressure and context switching between clusters.
Most candidates who fail say they ran out of time — not that they didn't know the answers.

---

**Q: Do I need to know all 5 domains equally?**
No. Focus on Troubleshooting (30%) and Cluster Architecture (25%) first.
Together that's 55% of your score. Nail those two and the rest becomes buffer.

---

**Q: What happens if I can't complete a question?**
Skip it. Flag it. Come back at the end.
Leaving a question blank is better than spending 20 minutes on it and missing 3 easier ones.

---

**Q: Is minikube enough for practice?**
For Phase 1 and 2 questions — yes, completely.
For Phase 3 (kubeadm, multi-node, cluster upgrades) — use kind with a multi-node config or a real multi-node setup.

---

**Q: What version of Kubernetes is on the exam?**
Check the official CNCF CKA page before your exam — it changes periodically.
As of 2026, the exam uses Kubernetes v1.31.

---

**Q: How is the exam scored?**
Automatically — by checking the state of your cluster after each task.
Your commands don't matter. Your results do.

---

**Q: Can I use vim or nano?**
Both are available. vim is faster once you're comfortable.
Add the vimrc config from `00-environment-setup/aliases.md` to avoid YAML indentation pain.

---

**Q: What's the most important thing to practice?**
Troubleshooting. It's 30% of the exam and the area most people underestimate.
Practice `describe` and `logs --previous` until it's completely automatic.
