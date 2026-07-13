---
title: "Week 5 Worklog"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

**Period:** 18/05/2026 – 20/05/2026

### Week 5 Objectives:

* Practice cloud storage: S3, RDS, DynamoDB, ElastiCache.
* Choose the right storage option by use case, cost and performance.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| Mon | Lab 1: S3 Static Website Hosting — upload HTML/CSS/JS, enable hosting, public-read Bucket Policy. Lab 2: Deploy RDS MySQL in Private Subnet with Multi-AZ; connect from EC2 and run CRUD. | 18/05/2026 | 18/05/2026 | <https://000057.awsstudygroup.com/><br><https://000005.awsstudygroup.com/> |
| Tue | Lab 3: Create DynamoDB table (Partition/Sort Key); PutItem, GetItem, Query, Scan; compare GSI. | 19/05/2026 | 19/05/2026 | <https://000060.awsstudygroup.com/><br><https://000039.awsstudygroup.com/> |
| Wed | Lab 4: Deploy ElastiCache Redis and cache RDS queries (latency ~50ms → ~2ms). Summarize S3 / RDS / DynamoDB / ElastiCache trade-offs; verify RDS ← EC2 Security Group rules. | 20/05/2026 | 20/05/2026 | <https://000061.awsstudygroup.com/><br><https://cloudjourney.awsstudygroup.com/> |

### Week 5 Achievements:

* Hosted a static website on S3.
* Deployed Multi-AZ RDS and practiced DynamoDB with GSI.
* Reduced query latency ~25x using ElastiCache Redis.

### Challenges & Solutions:

* EC2 could not reach RDS because the RDS Security Group blocked inbound from the EC2 SG → fixed inbound rules.

### Next Week Plan:

* Learn serverless architecture with AWS Lambda and API Gateway.
