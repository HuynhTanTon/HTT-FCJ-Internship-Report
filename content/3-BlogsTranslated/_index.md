---
title: "Translated Blogs"
date: 2026-07-14
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

# Translated Blogs

This section presents translated / summarized official AWS technical articles (Compute Blog, News Blog, Database Blog, Cloud Operations Blog, and Documentation). They were chosen because they map directly to the URL Shortener architecture deployed in the Workshop section: **S3 + Lambda Function URL + DynamoDB + CloudWatch**.

Each entry lists the source, main content, and a reflection tied to this internship project.

### [Blog 1 – Build a Serverless, Private URL Shortener](3.1-Blog1/)

Summary of AWS guidance for a serverless URL shortener (Lambda + S3 + API Gateway), compared with my Function URL + DynamoDB design.

### [Blog 2 – Announcing AWS Lambda Function URLs](3.2-Blog2/)

Summary of Lambda Function URLs — built-in HTTPS endpoints for a single function — the backend approach I used instead of API Gateway.

### [Blog 3 – Tutorial: Configuring a static website on Amazon S3](3.3-Blog3/)

Summary of the official static website hosting tutorial (Block Public Access and Bucket Policy) — matching frontend work in section 5.4.

### [Blog 4 – Implement resource counters with Amazon DynamoDB](3.4-Blog4/)

Summary of DynamoDB resource-counter patterns, focusing on atomic counters / `UpdateItem` — matching `clickCount` on redirect.

### [Blog 5 – How to get notified on specific Lambda function error patterns using CloudWatch](3.5-Blog5/)

Summary of alerting on Lambda log error patterns via CloudWatch — related to the metric filter + alarm + SNS setup in section 5.5.
