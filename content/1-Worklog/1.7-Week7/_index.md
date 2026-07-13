---
title: "Week 7 Worklog"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

**Period:** 01/06/2026 – 07/06/2026

### Week 7 Objectives:

* Practice Infrastructure as Code with CloudFormation and CDK.
* Build a CI/CD pipeline and use Systems Manager Session Manager for secure access.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| Mon | Lab 1: Write CloudFormation YAML to deploy VPC, 2 Subnets, Security Group, EC2 with one CLI command. | 01/06/2026 | 01/06/2026 | <https://000037.awsstudygroup.com/><br><https://000102.awsstudygroup.com/> |
| Tue | Lab 2: Init a TypeScript CDK app with S3 + Lambda; run `cdk bootstrap`, `cdk synth`, `cdk deploy`. | 02/06/2026 | 02/06/2026 | <https://000038.awsstudygroup.com/><br><https://000076.awsstudygroup.com/> |
| Wed | Lab 3: Build CodePipeline — Source (CodeCommit) → Build (CodeBuild) → Deploy (CloudFormation). | 03/06/2026 | 04/06/2026 | <https://000023.awsstudygroup.com/><br><https://000084.awsstudygroup.com/> |
| Thu | Lab 4: Connect to EC2 without public IP / without opening port 22 using SSM Session Manager. | 05/06/2026 | 05/06/2026 | <https://000058.awsstudygroup.com/><br><https://000031.awsstudygroup.com/> |
| Fri | Review IaC value (version control, reuse, automation); verify the pipeline after each push. | 06/06/2026 | 06/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Week 7 Achievements:

* Deployed infrastructure with CloudFormation and CDK.
* Built an end-to-end CI/CD pipeline.
* Accessed EC2 securely via Session Manager without SSH.

### Challenges & Solutions:

* First CDK deploy failed because the account was not bootstrapped → ran `cdk bootstrap` then redeployed.

### Next Week Plan:

* Learn Container Services: Docker, Amazon ECS and Fargate.
