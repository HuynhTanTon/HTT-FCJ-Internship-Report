---
title: "Week 3 Worklog"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

**Period:** 04/05/2026 – 06/05/2026

### Week 3 Objectives:

* Design and deploy networking with Amazon VPC.
* Configure public/private subnets, IGW, NAT Gateway, Security Groups and NACLs.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| Mon | Study VPC architecture (CIDR, Subnet, Route Table, IGW). Lab 1: Deploy VPC 10.0.0.0/16, create Public & Private Subnets, configure Internet Gateway. | 04/05/2026 | 04/05/2026 | <https://000003.awsstudygroup.com/> |
| Tue | Configure NAT Gateway for private subnets; compare Security Groups (stateful) vs NACLs (stateless). | 05/05/2026 | 05/05/2026 | <https://000003.awsstudygroup.com/> |
| Wed | Lab 2: Networking Workshop — multi-tier (web public, DB private); debug Route Tables / NAT; verify private subnet internet access via NAT Gateway. | 06/05/2026 | 06/05/2026 | <https://000092.awsstudygroup.com/><br><https://000003.awsstudygroup.com/> |

### Week 3 Achievements:

* Deployed a VPC with public/private subnets, IGW and NAT Gateway.
* Understood traffic flow via Route Tables.
* Distinguished Security Groups from Network ACLs.

### Challenges & Solutions:

* NAT Gateway failed due to a missing private subnet route → debugged Route Tables using the lab docs.

### Next Week Plan:

* Learn Amazon EC2 — launch instances and configure Auto Scaling.
