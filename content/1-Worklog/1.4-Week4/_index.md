---
title: "Week 4 Worklog"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

**Period:** 11/05/2026 – 17/05/2026

### Week 4 Objectives:

* Launch and manage Amazon EC2.
* Configure Auto Scaling and monitor with CloudWatch.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| Mon | Lab 1: Launch EC2 (Amazon Linux 2), install Apache, open ports 80/443, access via Public IP. | 11/05/2026 | 11/05/2026 | <https://000004.awsstudygroup.com/> |
| Tue | Study AMI, Key Pair, Elastic IP; secure SSH Security Group (personal IP only). | 12/05/2026 | 12/05/2026 | <https://000004.awsstudygroup.com/> |
| Wed | Lab 2: Create Launch Template and Auto Scaling Group (min=1, max=3) with CPU-based scaling. | 13/05/2026 | 13/05/2026 | <https://000006.awsstudygroup.com/> |
| Thu | Lab 3: Build CloudWatch Dashboard (CPU, Network, StatusCheck); Alarm + SNS when CPU > 70%. | 14/05/2026 | 14/05/2026 | <https://000036.awsstudygroup.com/><br><https://000008.awsstudygroup.com/> |
| Fri | Validate Auto Scaling under load; review EC2 lifecycle (launch/stop/start/terminate). | 15/05/2026 | 15/05/2026 | <https://000006.awsstudygroup.com/><br><https://000004.awsstudygroup.com/> |

### Week 4 Achievements:

* Mastered the EC2 lifecycle and deployed a web server on cloud.
* Configured CPU-based Auto Scaling.
* Set up proactive monitoring with CloudWatch + SNS.

### Challenges & Solutions:

* SSH failed because port 22 was closed → added inbound SSH for personal IP only (not 0.0.0.0/0).

### Next Week Plan:

* Learn storage services: Amazon S3, RDS and DynamoDB.
