---
title: "Clean up resources"
date: 2026-07-14
weight: 6
chapter: false
pre: " 5.6. "
---

#### Summary

After finishing the deployment, I had a serverless URL shortener on AWS with **S3** (frontend), **Lambda Function URL** (backend), **DynamoDB** (storage), and error monitoring via **CloudWatch** / SNS. This section lists resources to tear down after the demo to avoid ongoing charges.

#### Resources to clean up

1. Lambda function `url-shortener-backend` (including Function URL).
2. DynamoDB table `url-shortener-links`.
3. All objects in S3 bucket `url-shortener-frontend-forward`, then delete the bucket.
4. The IAM role attached to Lambda (for example the deleted role `url-shortener-backend-role-...` or `url-shortener-lambda-role`) and its DynamoDB policy.
5. CloudWatch Alarm `url-shortener-error-alarm`, Metric filter, and Log group `/aws/lambda/url-shortener-backend`.
6. SNS topic used for alerts.

![cleanup](/images/5-Workshop/5.6-Don-dep/cleanup.png)
