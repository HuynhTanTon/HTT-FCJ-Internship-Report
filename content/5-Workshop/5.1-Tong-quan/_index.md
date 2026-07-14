---
title: "Architecture overview"
date: 2026-07-14
weight: 1
chapter: false
pre: " 5.1. "
---

#### Objective

This section describes the architecture I chose for the serverless URL Shortener: AWS services involved, how they connect, and the runtime request flow after deployment.

#### How it works

1. The user opens the static site on **S3** (`index.html`) and pastes a long URL.
2. The frontend calls `POST /` on the **Lambda Function URL** with `{ "url": "..." }`.
3. Lambda generates a 6-character `shortCode`, stores it in **DynamoDB** (table `url-shortener-links`, partition key `shortCode`), and returns a `shortUrl`.
4. On `GET /{shortCode}`, Lambda looks up DynamoDB, increments `clickCount` (atomic via `UpdateCommand`), then returns **HTTP 302** to `originalUrl`.
5. `GET /stats/{shortCode}` returns stats without incrementing the counter.

![overview](/images/5-Workshop/5.1-Tong-quan/architecture.png)

#### Why this architecture

+ **Lambda Function URL** provides a public HTTPS endpoint for a simple API — no separate API Gateway.
+ **DynamoDB** fits key-value lookup by `shortCode`, on-demand, with no server administration.
+ **S3 Static Website Hosting** serves the static frontend cheaply and scales automatically.
