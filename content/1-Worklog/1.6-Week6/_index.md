---
title: "Week 6 Worklog"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

**Period:** 25/05/2026 – 31/05/2026

### Week 6 Objectives:

* Build serverless apps with Lambda, API Gateway and Step Functions.
* Understand event-driven architecture and pay-per-invocation billing.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| Mon | Lab 1: Write a Python Lambda to delete EC2 snapshots older than 30 days; EventBridge trigger at 2:00 AM. | 25/05/2026 | 25/05/2026 | <https://000022.awsstudygroup.com/><br><https://000066.awsstudygroup.com/> |
| Tue | Lab 2: Build Book Store REST API — API Gateway + Lambda + DynamoDB (CRUD, proper JSON status codes). | 26/05/2026 | 27/05/2026 | <https://000078.awsstudygroup.com/><br><https://000066.awsstudygroup.com/> |
| Wed | Continue Book Store backend; integrate S3 if needed; validate API responses. | 28/05/2026 | 28/05/2026 | <https://000078.awsstudygroup.com/><br><https://000079.awsstudygroup.com/> |
| Thu | Lab 3: Step Functions — ValidateOrder → ProcessPayment → UpdateInventory → SendNotification. | 29/05/2026 | 29/05/2026 | <https://000047.awsstudygroup.com/> |
| Fri | Test error handling / retry; tune Lambda timeout (3s → 30s) and reduce cold start. | 30/05/2026 | 30/05/2026 | <https://000047.awsstudygroup.com/><br><https://000077.awsstudygroup.com/> |

### Week 6 Achievements:

* Understood event-driven architecture and serverless benefits.
* Built a Book Store REST API with API Gateway + Lambda + DynamoDB.
* Designed a multi-step workflow with Step Functions (error handling, retry).

### Challenges & Solutions:

* Lambda timed out with the default 3s limit → increased timeout to 30s and optimized code to reduce cold start.

### Next Week Plan:

* Learn Infrastructure as Code with CloudFormation, CDK and CI/CD pipelines.
