---
title: "Deploy Backend"
date: 2026-07-14
weight: 3
chapter: false
pre: " 5.3. "
---

#### Goal

Deploy the business layer: Lambda receives HTTPS requests via Function URL, reads/writes DynamoDB, and returns JSON or a 302 redirect.

#### What I did

1. Created `url-shortener-backend` (Node.js 20.x) with an execution role that can access DynamoDB.
2. Implemented handler logic: `POST /`, `GET /{shortCode}`, `GET /stats/{shortCode}`, plus CORS/OPTIONS.
3. Enabled Function URL (Auth `NONE` + CORS).
4. Verified with curl/PowerShell and checked items in DynamoDB.

Details:

- [Create Lambda function & Function URL](5.3.1-tao-lambda/)
- [Test API](5.3.2-test-lambda/)
