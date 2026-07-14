---
title: "Cấu hình Bucket Policy cho phép đọc công khai"
date: 2026-07-14
weight: 2
chapter: false
pre: " 5.4.2. "
---

Để Static Website Hosting phục vụ được `index.html` công khai, mình cấu hình **Bucket Policy** chỉ cấp `s3:GetObject` (không list/write):

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

Các bước thực hiện: **S3** → bucket `url-shortener-frontend-forward` → tab **Permissions** → **Bucket policy** → Edit → Save. Trước đó cần tắt Block Public Access phù hợp để policy public read có hiệu lực.
