---
title: "S3 Static Website"
date: 2026-07-14
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Tutorial: Configuring a static website on Amazon S3

#### 1. Source information

| Item | Details |
| --- | --- |
| Original title | Tutorial: Configuring a static website on Amazon S3 |
| Source | [Amazon S3 User Guide](https://docs.aws.amazon.com/AmazonS3/latest/userguide/HostingWebsiteOnS3Setup.html) |
| Topics | Static Website Hosting, Block Public Access, Bucket Policy, website endpoint |

#### 2. Summary

The official tutorial walks through turning an S3 bucket into a static site: create the bucket, enable Static website hosting with `index.html`, adjust Block Public Access, attach a public `GetObject` Bucket Policy, upload content, then test via the **website endpoint**. AWS notes the default endpoint is **HTTP**; production should consider CloudFront (+ HTTPS) and Origin Access Control instead of a public bucket when keeping Block Public Access enabled.

#### 3. Main content

**3.1. Enable hosting** — Properties → Static website hosting → Enabled; Index document = `index.html` (case-sensitive).

**3.2. Public access** — adjust Block Public Access; policy with `Principal: "*"` and `s3:GetObject` on `arn:aws:s3:::bucket/*`.

**3.3. Testing** — use the website endpoint (not the REST endpoint). Wrong Content-Type or missing policy → 403 / Access Denied.

**3.4. HTTP limitation** — docs recommend CloudFront for HTTPS, custom domains, and stronger security headers.

#### 4. Reflection (project link)

This matches the checklist I completed in **section 5.4**:

1. Bucket `url-shortener-frontend-forward`
2. Enable Static website hosting
3. Public-read Bucket Policy (`GetObject`)
4. Upload `index.html`, `config.js`, background image
5. End-to-end test on the website endpoint

Key learning from the docs: the clear line between **website endpoint** and **REST endpoint**, plus the HTTP limit — useful when explaining lab limits and next steps (CloudFront + ACM).
