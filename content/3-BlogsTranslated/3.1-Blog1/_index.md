---
title: "Serverless URL Shortener"
date: 2026-07-14
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Build a Serverless, Private URL Shortener

#### 1. Source information

| Item | Details |
| --- | --- |
| Original title | Build a Serverless, Private URL Shortener |
| Source | [AWS Compute Blog](https://aws.amazon.com/blogs/compute/build-a-serverless-private-url-shortener/) |
| Topics | Serverless URL shortener, Lambda, API Gateway, S3 |

#### 2. Summary

The article shows how to build a private serverless URL shortener without managing servers. The key idea is using **S3 Static Website Hosting as a redirection engine**: each short link is a (often empty) object with website-redirect metadata to the long URL. Opening the short URL makes S3 return an HTTP redirect without application code at redirect time.

Creating short links uses a static admin page on S3; Shorten triggers **API Gateway → Lambda**. Lambda generates a random short id and stores an S3 object with redirect metadata. CloudFront (and a sample CloudFormation stack) can wrap the solution for a unified edge endpoint.

#### 3. Main content

**3.1. S3 as redirection engine** — enable website hosting; each short code is an object key with redirect metadata; S3 serves the redirect on the website endpoint.

**3.2. Create via API** — static frontend POSTs to API Gateway; Lambda validates, creates a random key, PutObject with redirect metadata, returns the short URL.

**3.3. Optional pieces** — CloudFront for CDN/custom domain; CloudFormation packages S3, Lambda, API Gateway, and helpers.

#### 4. Reflection (project link)

Same problem domain, different design from my workshop:

| Item | AWS Compute Blog | My workshop |
| --- | --- | --- |
| Mapping store | S3 object + redirect metadata | DynamoDB `url-shortener-links` |
| Redirect | S3 website redirect | Lambda **HTTP 302** |
| Ingress API | API Gateway | **Lambda Function URL** |
| Click counting | Not the focus | Atomic `clickCount` on redirect |

S3 redirects are lean for “shorten + redirect only.” I chose Lambda + DynamoDB for **click counts**, a **stats** API, and a clear split between S3 frontend and Function URL backend. The article clarifies the trade-off: less code with S3 redirects, but harder to grow app logic (stats, conditional 404, centralized error handling) in one API layer like Function URL.
