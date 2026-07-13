---
title: "Week 8 Worklog"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

**Period:** 08/06/2026 – 10/06/2026

### Week 8 Objectives:

* Containerize apps with Docker and deploy on Amazon ECS / Fargate.
* Understand EC2 launch type vs Fargate.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| Mon | Lab 1: Write a Dockerfile for a Node.js app, build locally, push the image to Amazon ECR. | 08/06/2026 | 08/06/2026 | <https://000015.awsstudygroup.com/> |
| Tue | Lab 2: Create ECS Cluster, Task Definition (ECR image), ECS Service with 2 tasks + ALB; configure resource limits, environment variables; fix IAM Role for ECR pull. | 09/06/2026 | 09/06/2026 | <https://000016.awsstudygroup.com/><br><https://000017.awsstudygroup.com/> |
| Wed | Lab 3: Switch to Fargate launch type — no EC2 management, pay by vCPU/memory; compare EC2 launch type vs Fargate and verify stability. | 10/06/2026 | 10/06/2026 | <https://000067.awsstudygroup.com/><br><https://000016.awsstudygroup.com/> |

### Week 8 Achievements:

* Completed the flow Dockerfile → build → ECR → ECS.
* Deployed an ECS Service with ALB and 2 tasks.
* Ran the app on Fargate without managing servers.

### Challenges & Solutions:

* ECS Service failed because Task Execution Role lacked ECR pull permission → attached `AmazonEC2ContainerRegistryReadOnly`.

### Next Week Plan:

* Learn Amazon EKS — deploy and manage a Kubernetes cluster on AWS.
