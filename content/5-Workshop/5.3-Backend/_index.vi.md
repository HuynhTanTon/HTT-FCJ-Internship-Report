---
title: "Triển khai Backend"
date: 2026-07-14
weight: 3
chapter: false
pre: " 5.3. "
---

#### Mục tiêu

Triển khai lớp xử lý nghiệp vụ: Lambda nhận HTTPS request qua Function URL, đọc/ghi DynamoDB, trả JSON hoặc redirect 302.

#### Việc đã làm

1. Tạo function `url-shortener-backend` (Node.js 20.x), gắn execution role có quyền DynamoDB.
2. Triển khai logic handler: `POST /`, `GET /{shortCode}`, `GET /stats/{shortCode}`, xử lý CORS/OPTIONS.
3. Bật Function URL (Auth `NONE` + CORS).
4. Kiểm thử bằng curl/PowerShell và đối chiếu dữ liệu trên DynamoDB.

Chi tiết từng bước:

- [Tạo Lambda function & Function URL](5.3.1-tao-lambda/)
- [Test API](5.3.2-test-lambda/)
