# ⏰ Time Management

The CKA exam is won or lost on time. Most failures are not about knowledge — they're about running out of time.

---

## The Rule of 10

**Never spend more than 10 minutes on a single question.**

If you're stuck at the 8-minute mark — skip it, flag it, move on.
You can come back. You cannot get those minutes back.

---

## The First 5 Minutes

Before solving anything:
1. Set aliases and autocomplete (60 seconds)
2. Scan every question (3–4 minutes)
3. Tag: easy ones, hard ones, high-weight ones

This investment saves 20+ minutes over the exam.

---

## Question Priority Order

```
High weight + Easy   → Do first
Low weight + Easy    → Do second
High weight + Hard   → Do third (with time cap)
Low weight + Hard    → Do last / skip if needed
```

Don't do questions in order. Do them in priority order.

---

## Per-Question Time Budget

| Weight | Time to Spend |
|--------|--------------|
| 4–5% | 4–5 minutes |
| 6–7% | 6–8 minutes |
| 8–10% | 8–10 minutes |
| Any | Hard cap: 10 minutes max |

---

## The `--force` Habit

```bash
# Instead of waiting for graceful termination (30s default)
kubectl delete pod <n> --force --grace-period=0
```

This alone saves 2–3 minutes across a full exam.

---

## Verification Time Budget

Each verification should take **under 60 seconds**:

```bash
kubectl get pod <n> -n <ns>          # 5 seconds
kubectl get endpoints <svc> -n <ns>  # 5 seconds
kubectl auth can-i get pods --as=<user> -n <ns>   # 5 seconds
```

Don't over-verify. One check per task is enough.
