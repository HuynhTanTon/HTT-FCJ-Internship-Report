---
title: "Architecture overview"
date: 2026-07-14
weight: 1
chapter: false
pre: " 5.1. "
---

#### Goal of this section

Describe the architecture I actually deployed: AWS components, how they call each other, and what each Function URL API does.

#### System architecture diagram

Architecture deployed in **ap-southeast-1**: S3 (Static Website) + Lambda Function URL (Node.js) + DynamoDB (URL mapping) + IAM Least Privilege, plus CloudWatch / SNS error alerts.

![Serverless URL Shortener architecture](/images/5-Workshop/5.1-Tong-quan/architecture.png)

**Main flows on the diagram:**

1. User opens the S3-hosted website.
2. Frontend calls the API via Lambda Function URL.
3. Lambda reads/writes the DynamoDB mapping table (assuming an IAM role).
4. Lambda returns a response (create JSON or HTTP 302 redirect).
5. Error logs/metrics → CloudWatch Alarm → SNS → admin email when the threshold is crossed.

When opening a short link, the browser calls the Function URL directly (`GET /{shortCode}`); Lambda returns **302** with `Location` to `originalUrl`. The S3 frontend is not involved in that redirect step.

#### API design

| Method & path | Purpose | DynamoDB write | Affects clicks |
| ------------- | -------- | ------------ | --------------- |
| `POST /` | Create short link | `PutItem` | No |
| `GET /{shortCode}` | Redirect to original URL | `UpdateItem` (increment `clickCount`) | Yes |
| `GET /stats/{shortCode}` | Read stats | read path | No |

Create flow: S3 UI → `config.js` Function URL → `POST /` → store item → return `{ shortCode, shortUrl, originalUrl }`.

Redirect flow: `GET /{shortCode}` → atomic click update if code exists (else 404) → **302** to `originalUrl`.

#### Why Function URL instead of API Gateway

- One simple HTTPS API with Auth `NONE` + CORS is enough for the lab.
- Fewer resources to configure and clean up.
- Lower cost/complexity for an internship demo.

Trade-off: Function URL has fewer management features than API Gateway (advanced throttling, API keys, usage plans). Acceptable for this shortener lab.

#### Why DynamoDB

The core problem is **lookup by key** `shortCode` → `originalUrl`. On-demand DynamoDB fits: no capacity guessing, low latency, no RDS-style instance ops.

#### Outcome

With all three layers up, the closed loop works: create on S3 UI → store in DynamoDB → open short URL via Lambda → redirect + count clicks → inspect stats / table items.
