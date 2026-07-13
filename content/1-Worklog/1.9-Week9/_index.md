---
title: "Week 9 Worklog"
date: 2024-01-01
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

**Period:** 15/06/2026 – 21/06/2026

### Week 9 Objectives:

* Create and manage an Amazon EKS cluster.
* Practice Kubernetes: Pods, Deployments, Services, ConfigMaps, Helm.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| Mon | Study Kubernetes architecture: Control Plane, Worker Nodes, etcd; install `eksctl` and `kubectl`. | 15/06/2026 | 15/06/2026 | <https://000126.awsstudygroup.com/><br><https://000065.awsstudygroup.com/> |
| Tue | Lab 1: Create an EKS Cluster with `eksctl`, configure kubectl, verify node group (`kubectl get nodes`). | 16/06/2026 | 17/06/2026 | <https://000062.awsstudygroup.com/><br><https://000065.awsstudygroup.com/> |
| Wed | Practice Deployment / Service (ClusterIP, NodePort, LoadBalancer); observe Pod lifecycle. | 18/06/2026 | 18/06/2026 | <https://000126.awsstudygroup.com/> |
| Thu | Debug CrashLoopBackOff with `kubectl logs` and `kubectl describe`; check required environment variables. | 19/06/2026 | 19/06/2026 | <https://000126.awsstudygroup.com/><br><https://000062.awsstudygroup.com/> |
| Fri | Review Deployment self-healing and reconciliation loop; summarize ECS vs EKS. | 20/06/2026 | 20/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Week 9 Achievements:

* Created an EKS cluster and connected with kubectl.
* Understood Pod lifecycle, Deployment self-healing and Service types.
* Debugged CrashLoopBackOff caused by a missing required environment variable.

### Challenges & Solutions:

* Pods stuck in CrashLoopBackOff → used `kubectl logs` / `describe` and found a missing required env var.

### Next Week Plan:

* Learn Data & Analytics: Athena, Glue and QuickSight.
