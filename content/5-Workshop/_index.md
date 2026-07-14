---
title: "Workshop"
date: 2026-07-14
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Serverless URL Shortener on AWS

#### Overview

Section 5 records how I deployed a fully **serverless URL Shortener** on AWS. It is written as a technical report: goals, chosen architecture, steps performed, and results achieved.

The app has three layers: a static UI on **Amazon S3**, business logic on **AWS Lambda (Function URL)**, and storage on **Amazon DynamoDB**. Everything runs in **ap-southeast-1 (Singapore)**, with no servers to manage and no separate API Gateway.

#### What was deployed

- **Frontend**: S3 bucket `url-shortener-frontend-forward` with Static Website Hosting serving `index.html` / `config.js`.
- **Backend**: Lambda `url-shortener-backend` via Function URL (`POST /` create, `GET /{shortCode}` 302 redirect, `GET /stats/{shortCode}` stats).
- **Data**: DynamoDB table `url-shortener-links` (partition key `shortCode`) with `originalUrl`, `clickCount`, `createdAt`; on-demand capacity.
- **Monitoring (advanced)**: atomic click counting on redirect; Metric filter + CloudWatch Alarm + SNS on `[ERROR]` logs.

#### Section 5 structure

1. [Architecture overview](5.1-Tong-quan/) — end-to-end flow and why S3 + Lambda Function URL + DynamoDB were chosen.
2. [Prerequisites](5.2-Chuan-bi/) — fixed resource names and the IAM role/policy created for Lambda.
3. [Deploy Backend](5.3-Backend/) — Lambda, Function URL, and API / DynamoDB verification.
4. [Deploy Frontend](5.4-Frontend/) — S3 Static Website, Bucket Policy, upload, and end-to-end test.
5. [Advanced (bonus)](5.5-Nang-cao/) — atomic `clickCount` and CloudWatch / SNS alerts.
6. [Clean up resources](5.6-Don-dep/) — resources to tear down after the demo to avoid ongoing charges.
