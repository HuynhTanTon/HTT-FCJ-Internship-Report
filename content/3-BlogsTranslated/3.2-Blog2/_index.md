---
title: "Lambda Function URLs"
date: 2026-07-14
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Announcing AWS Lambda Function URLs

#### 1. Source information

| Item | Details |
| --- | --- |
| Original title | Announcing AWS Lambda Function URLs: Built-in HTTPS Endpoints for Single-Function Microservices |
| Source | [AWS News Blog](https://aws.amazon.com/blogs/aws/announcing-aws-lambda-function-urls-built-in-https-endpoints-for-single-function-microservices/) |
| Topics | Lambda Function URL, HTTPS endpoint, CORS, vs API Gateway |

#### 2. Summary

AWS announced **Lambda Function URLs**: built-in HTTPS endpoints for a single Lambda function, with optional CORS, without requiring API Gateway or an ALB. The endpoint attaches to an alias/`$LATEST` and can be created via console, SDKs, or CloudFormation / SAM / CDK. Auth defaults to IAM; `NONE` enables a public endpoint (with resource-based policy updates). There is no separate fee beyond normal Lambda invoke cost.

#### 3. Main content

**3.1. When Function URLs fit** — single-function microservices that need a public endpoint without API Gateway advanced features (validation, fine throttling, custom authorizers, custom domains, usage plans, caching). Examples: webhooks, form validators, simple inference, fast R&D.

**3.2. When to prefer API Gateway** — platform-level API management/security features that Function URLs do not fully replace.

**3.3. CORS and access** — native CORS configuration matters when a frontend on another origin calls the API (S3 website → Function URL).

#### 4. Reflection (project link)

This article explains the **exact backend mechanism** used in my shortener: one function `url-shortener-backend` serving `POST /`, `GET /{code}`, `GET /stats/...` via Function URL, Auth `NONE`, CORS for the S3 frontend.

Compared with the Compute Blog shortener (API Gateway), Function URL reduced lab resources while still providing HTTPS. Trade-off accepted: no custom domain or advanced throttling yet — fine for the internship scope; production may add CloudFront / API Gateway as AWS suggests when needs grow.
