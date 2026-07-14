---
title: "Deploy Backend"
date: 2026-07-14
weight: 3
chapter: false
pre: " 5.3. "
---

#### Serverless backend

In this section I deployed Lambda `url-shortener-backend`, attached the IAM role created earlier, deployed the handler (`handler.mjs` / `index.mjs`), and enabled a Function URL so the frontend can call the API directly — without API Gateway.

#### What I completed

- [Create Lambda function & Function URL](5.3.1-tao-lambda/)
- [Test API](5.3.2-test-lambda/)
