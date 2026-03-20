# 🎯 Exam Strategy

## The Exam in One Sentence

The CKA rewards candidates who are **fast, accurate, and calm under pressure** — not the ones who know the most theory.

---

## Before the Exam

**1 week before:**
- Do both mock exams under real 2-hour conditions
- Time yourself per question — anything over 10 minutes is a flag
- Identify your weak domains and drill those specifically

**Night before:**
- Don't cram. Review your cheatsheets once. Sleep.
- Prepare your environment: stable internet, quiet room, valid ID, water

**Day of:**
- Join the exam session 15 minutes early
- Room check takes time — don't be late

---

## The 2-Hour Game Plan

| Time | Action |
|------|--------|
| 0:00–0:05 | Set aliases, autocomplete, scan all questions |
| 0:05–1:30 | Solve questions in order of: easy + high weight first |
| 1:30–1:50 | Return to flagged/skipped questions |
| 1:50–2:00 | Final verification pass — re-check your answers |

---

## How to Read a Question

Every CKA question follows a pattern:

```
[Context to switch to]
[Namespace to work in]
[The task]
[Success criteria]
```

**Read in this order:**
1. Context (switch immediately)
2. Namespace (set it or use -n)
3. Task (what to do)
4. Success criteria (how to verify)

---

## When to Use YAML vs Imperative

**Use imperative when:**
- Creating simple resources: pod, deployment, service, role, rolebinding
- You know the flags — it's 5x faster

**Use YAML when:**
- Complex spec: volumes, multi-container, probes, affinity
- Fixing an existing broken resource
- You need `--dry-run=client -o yaml` to generate and edit

---

## The Mental Model for Troubleshooting Questions

```
get → describe → logs → fix → verify
```

Never skip a step. The answer is almost always in `describe` events or `logs --previous`.

---

## How to Handle Being Stuck

1. `describe` the resource — read every line of the Events section
2. `logs --previous` — read the last crash output
3. Check the obvious: namespace, image tag, selector labels, ports
4. If still stuck after 8 minutes — **skip and flag**
5. Move to the next question — a fresh question beats a stuck one

---

## Post-Exam

- Results are available within 24 hours
- If you fail, 1 free retake is included — use it
- Note which questions you struggled with and target those domains
