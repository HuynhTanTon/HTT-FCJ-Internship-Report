---
title: "Configure Bucket Policy for public read"
date: 2026-07-14
weight: 2
chapter: false
pre: " 5.4.2. "
---

To make Static Website Hosting serve `index.html` publicly, I configured a **Bucket Policy** with only `s3:GetObject` (no list/write):

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::url-shortener-frontend-forward/*"
    }
  ]
}
```

Steps: **S3** → bucket `url-shortener-frontend-forward` → **Permissions** → **Bucket policy** → Edit → Save. Block Public Access settings were adjusted as needed so the public-read policy could take effect.
