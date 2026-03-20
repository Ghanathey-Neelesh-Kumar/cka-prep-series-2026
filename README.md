<div align="center">

# 🔥 CKA 2026 Series
### The Most Hands-On CKA Preparation Repository on GitHub

**Stop reading. Start breaking things. Start fixing them.**

[![YouTube](https://img.shields.io/badge/YouTube-Subscribe-red?style=for-the-badge&logo=youtube)](https://youtube.com/@YOUR_CHANNEL)
[![GitHub Stars](https://img.shields.io/github/stars/YOUR_USERNAME/cka-2026-series?style=for-the-badge&logo=github)](https://github.com/YOUR_USERNAME/cka-2026-series/stargazers)
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-brightgreen?style=for-the-badge)](./CONTRIBUTING.md)
[![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](LICENSE)

</div>

---

## 🎯 What Makes This Different

Most CKA resources teach you Kubernetes.
This repo trains you to **pass the CKA exam**.

There is a difference.

The CKA is a **2-hour, 100% hands-on, live-cluster exam**. No multiple choice. No theory questions. You type commands. You fix broken clusters. You get scored on results.

Every question in this repo follows one format:

```
🔴 A broken cluster/manifest is handed to you
⏱️  You have a time limit — just like the real exam
🔧 You investigate, diagnose, and fix it
✅ You verify it works
```

No spoon-feeding. No watching someone else type. **You fix it.**

---

## 🗺️ How This Repo Is Organised

```
cka-2026-series/
├── 00-environment-setup/     ← Set up minikube or kind. Start here.
├── question-bank/            ← The heart of the repo. 50+ exam questions.
│   ├── troubleshooting/      ← 30% of exam weight
│   ├── services-networking/  ← 20% of exam weight
│   ├── workloads-scheduling/ ← 15% of exam weight
│   ├── storage/              ← 10% of exam weight
│   ├── cluster-architecture/ ← 25% of exam weight
│   └── lightning-round/      ← Speed drills, multiple questions, timed
├── mock-exams/               ← Full 2-hour simulated exams
├── cheatsheets/              ← kubectl, YAML templates, common mistakes
├── misc/                     ← Exam strategy, time management, FAQ
└── assets/                   ← Diagrams and visual references
```

---

## 🚦 Where to Start

| Your Situation | Start Here |
|---------------|------------|
| Just getting started | [00 — Environment Setup](./00-environment-setup/) |
| Cluster is ready, let's practice | [Troubleshooting → Basic](./question-bank/troubleshooting/01-basic/) |
| Comfortable with basics | [Intermediate Questions](./question-bank/troubleshooting/02-intermediate/) |
| Exam in < 2 weeks | [Mock Exams](./mock-exams/) + [Exam Strategy](./misc/exam-strategy.md) |
| Just need a reference | [Cheatsheets](./cheatsheets/) |

---

## 📊 Question Bank — Full Index

### 🔴 Troubleshooting — 30% of Exam

> The single highest-weighted domain. We have the most questions here.

#### Basic
| # | Question | Topic | Video |
|---|----------|-------|-------|
| 01 | [Pod CrashLoopBackOff](./question-bank/troubleshooting/01-basic/01-pod-crashloop/) | Pod debugging | [▶ Watch](#) |

#### Intermediate
| # | Question | Topic | Video |
|---|----------|-------|-------|
| 01 | [Node NotReady](./question-bank/troubleshooting/02-intermediate/01-node-notready/) | Node debugging | Coming Soon |
| 02 | [Service Not Routing Traffic](./question-bank/troubleshooting/02-intermediate/02-service-routing/) | Service debug | Coming Soon |
| 03 | [DNS Failing Inside Pod](./question-bank/troubleshooting/02-intermediate/03-dns-failure/) | CoreDNS | Coming Soon |

#### Advanced
| # | Question | Topic | Video |
|---|----------|-------|-------|
| 01 | [Broken kube-apiserver](./question-bank/troubleshooting/03-advanced/01-broken-apiserver/) | Control plane | Coming Soon |
| 02 | [Broken kubelet on Worker](./question-bank/troubleshooting/03-advanced/02-broken-kubelet/) | Node repair | Coming Soon |
| 03 | [Full Cluster Meltdown](./question-bank/troubleshooting/03-advanced/03-cluster-meltdown/) | Mixed failures | Coming Soon |

---

### 🌐 Services & Networking — 20% of Exam

#### Basic
| # | Question | Topic | Video |
|---|----------|-------|-------|
| 01 | [Expose App with ClusterIP](./question-bank/services-networking/01-basic/01-clusterip/) | Services | Coming Soon |
| 02 | [NodePort Service](./question-bank/services-networking/01-basic/02-nodeport/) | Services | Coming Soon |

#### Intermediate
| # | Question | Topic | Video |
|---|----------|-------|-------|
| 01 | [Configure Ingress](./question-bank/services-networking/02-intermediate/01-ingress/) | Ingress | Coming Soon |
| 02 | [NetworkPolicy — Restrict Traffic](./question-bank/services-networking/02-intermediate/02-networkpolicy/) | NetworkPolicy | Coming Soon |

#### Advanced
| # | Question | Topic | Video |
|---|----------|-------|-------|
| 01 | [Debug Broken Ingress — 503](./question-bank/services-networking/03-advanced/01-ingress-503/) | Ingress debug | Coming Soon |
| 02 | [NetworkPolicy Blocking Traffic](./question-bank/services-networking/03-advanced/02-networkpolicy-debug/) | Network debug | Coming Soon |
| 03 | [Gateway API](./question-bank/services-networking/03-advanced/03-gateway-api/) | Gateway API | Coming Soon |

---

### ⚙️ Workloads & Scheduling — 15% of Exam

#### Basic
| # | Question | Topic | Video |
|---|----------|-------|-------|
| 01 | [Create & Manage a Deployment](./question-bank/workloads-scheduling/01-basic/01-deployment/) | Deployments | Coming Soon |
| 02 | [ConfigMaps & Secrets](./question-bank/workloads-scheduling/01-basic/02-configmaps-secrets/) | Config | Coming Soon |
| 03 | [Resource Requests & Limits](./question-bank/workloads-scheduling/01-basic/03-resource-limits/) | Resources | Coming Soon |

#### Intermediate
| # | Question | Topic | Video |
|---|----------|-------|-------|
| 01 | [Rolling Update & Rollback](./question-bank/workloads-scheduling/02-intermediate/01-rolling-update/) | Deployments | Coming Soon |
| 02 | [Taints & Tolerations](./question-bank/workloads-scheduling/02-intermediate/02-taints-tolerations/) | Scheduling | Coming Soon |
| 03 | [Node Affinity](./question-bank/workloads-scheduling/02-intermediate/03-node-affinity/) | Scheduling | Coming Soon |
| 04 | [Init Containers](./question-bank/workloads-scheduling/02-intermediate/04-init-containers/) | Workloads | Coming Soon |
| 05 | [Sidecar / Multi-Container Pods](./question-bank/workloads-scheduling/02-intermediate/05-sidecar/) | Workloads | Coming Soon |

#### Advanced
| # | Question | Topic | Video |
|---|----------|-------|-------|
| 01 | [StatefulSets](./question-bank/workloads-scheduling/03-advanced/01-statefulset/) | StatefulSets | Coming Soon |
| 02 | [DaemonSets](./question-bank/workloads-scheduling/03-advanced/02-daemonset/) | DaemonSets | Coming Soon |
| 03 | [CronJobs & Jobs](./question-bank/workloads-scheduling/03-advanced/03-cronjob/) | Jobs | Coming Soon |

---

### 💾 Storage — 10% of Exam

#### Basic
| # | Question | Topic | Video |
|---|----------|-------|-------|
| 01 | [PersistentVolume & PVC](./question-bank/storage/01-basic/01-pv-pvc/) | PV/PVC | Coming Soon |

#### Intermediate
| # | Question | Topic | Video |
|---|----------|-------|-------|
| 01 | [StorageClass & Dynamic Provisioning](./question-bank/storage/02-intermediate/01-storageclass/) | StorageClass | Coming Soon |
| 02 | [PVC in a StatefulSet](./question-bank/storage/02-intermediate/02-statefulset-pvc/) | Storage+StatefulSet | Coming Soon |

#### Advanced
| # | Question | Topic | Video |
|---|----------|-------|-------|
| 01 | [PVC Stuck in Pending — Debug It](./question-bank/storage/03-advanced/01-pvc-pending/) | Storage debug | Coming Soon |

---

### 🏗️ Cluster Architecture — 25% of Exam

#### Basic
| # | Question | Topic | Video |
|---|----------|-------|-------|
| 01 | [RBAC — Role & RoleBinding](./question-bank/cluster-architecture/01-basic/01-rbac-role/) | RBAC | Coming Soon |
| 02 | [Namespaces & ServiceAccounts](./question-bank/cluster-architecture/01-basic/02-namespaces-sa/) | Architecture | Coming Soon |

#### Intermediate
| # | Question | Topic | Video |
|---|----------|-------|-------|
| 01 | [ClusterRole & ClusterRoleBinding](./question-bank/cluster-architecture/02-intermediate/01-clusterrole/) | RBAC | Coming Soon |
| 02 | [kubeconfig — Multiple Clusters](./question-bank/cluster-architecture/02-intermediate/02-kubeconfig/) | kubeconfig | Coming Soon |
| 03 | [CertificateSigningRequest](./question-bank/cluster-architecture/02-intermediate/03-csr/) | TLS/CSR | Coming Soon |

#### Advanced
| # | Question | Topic | Video |
|---|----------|-------|-------|
| 01 | [etcd Backup & Restore](./question-bank/cluster-architecture/03-advanced/01-etcd-backup/) | etcd | Coming Soon |
| 02 | [Cluster Upgrade with kubeadm](./question-bank/cluster-architecture/03-advanced/02-cluster-upgrade/) | Upgrades | Coming Soon |
| 03 | [Install Cluster with kubeadm](./question-bank/cluster-architecture/03-advanced/03-kubeadm-install/) | kubeadm | Coming Soon |
| 04 | [TLS Certificates — Renew & Inspect](./question-bank/cluster-architecture/03-advanced/04-tls-certs/) | TLS/PKI | Coming Soon |

---

### ⚡ Lightning Round — Speed Drills

> Multiple questions. One timer. Pure exam pressure.

| # | Title | Questions | Time Limit | Video |
|---|-------|-----------|-----------|-------|
| 01 | [Basic Speed Drill](./question-bank/lightning-round/01-basic/01-basic-drill/) | 5 questions | 20 min | Coming Soon |
| 02 | [Intermediate Speed Drill](./question-bank/lightning-round/02-intermediate/01-intermediate-drill/) | 5 questions | 25 min | Coming Soon |
| 03 | [Advanced Speed Drill](./question-bank/lightning-round/03-advanced/01-advanced-drill/) | 5 questions | 30 min | Coming Soon |

---

## 📝 Mock Exams

| Exam | Questions | Duration | Difficulty |
|------|-----------|----------|-----------|
| [Mock Exam 1](./mock-exams/mock-exam-1/) | 17 tasks | 2 hours | Mixed |
| [Mock Exam 2](./mock-exams/mock-exam-2/) | 17 tasks | 2 hours | Mixed + Harder |

---

## 📚 Cheatsheets & References

| Resource | What's Inside |
|----------|--------------|
| [kubectl Cheatsheet](./cheatsheets/kubectl-cheatsheet.md) | Every command, organised for exam speed |
| [YAML Templates](./cheatsheets/yaml-templates.md) | Copy-paste ready templates for every resource |
| [Exam Tips](./cheatsheets/exam-tips.md) | The tactics that separate passers from failers |
| [Common Mistakes](./cheatsheets/common-mistakes.md) | The exact mistakes that cost people marks |

---

## 🧠 Misc

| Resource | What's Inside |
|----------|--------------|
| [Exam Strategy](./misc/exam-strategy.md) | How to approach the 2-hour exam |
| [Time Management](./misc/time-management.md) | Per-question timing and when to skip |
| [Mistakes to Avoid](./misc/mistakes-to-avoid.md) | Real mistakes from real candidates |
| [FAQ](./misc/faq.md) | Everything you've been Googling |

---

## ⭐ Star This Repo

If this is helping your CKA prep — star it.
It takes 1 second and helps other struggling candidates find this resource.

---

<div align="center">
<b>Every expert was once a beginner who refused to give up. 💪</b><br>
<i>New questions added every week alongside the YouTube series.</i>
</div>
