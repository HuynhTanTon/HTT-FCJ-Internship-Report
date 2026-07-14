---
title: "Architecture overview"
date: 2026-07-14
weight: 1
chapter: false
pre: " 5.1. "
---

#### Goal of this section

Describe the architecture I actually deployed: AWS components, how they call each other, and what each Function URL API does.

#### Logical architecture

```text
[ Browser ]
      │
      │ 1) open website endpoint
      ▼
[ S3 Static Website ]
  index.html + config.js
      │
      │ 2) fetch POST /  { "url": "..." }
      ▼
[ Lambda Function URL ]  url-shortener-backend
      │
      │ 3) PutItem / UpdateItem / GetItem
      ▼
[ DynamoDB ]  url-shortener-links
   PK: shortCode (S)
```

When a user opens a short link, the browser calls the Function URL directly (`GET /{shortCode}`); Lambda returns **302** with `Location` set to `originalUrl`. The S3 frontend is not involved in that redirect step.

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
