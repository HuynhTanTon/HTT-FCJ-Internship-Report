---
title: "Các bài blogs đã dịch"
date: 2026-07-14
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

# Các bài blogs đã dịch

Phần này trình bày bản dịch / tóm tắt các bài viết kỹ thuật chính thức từ AWS (Compute Blog, News Blog, Database Blog, Cloud Operations Blog và Documentation), được chọn vì **khớp trực tiếp** với kiến trúc URL Shortener mình đã triển khai ở mục Workshop: **S3 + Lambda Function URL + DynamoDB + CloudWatch**.

Mỗi mục nêu rõ nguồn gốc, nội dung chính và nhận xét liên hệ tới dự án báo cáo.

### [Blog 1 – Build a Serverless, Private URL Shortener](3.1-Blog1/)

Tóm tắt hướng dẫn xây URL shortener serverless trên AWS (Lambda + S3 + API Gateway) và so sánh với cách mình triển khai bằng Lambda Function URL + DynamoDB.

### [Blog 2 – Announcing AWS Lambda Function URLs](3.2-Blog2/)

Tóm tắt cơ chế Lambda Function URL — endpoint HTTPS gắn sẵn cho một hàm — đúng thành phần backend mình dùng thay cho API Gateway.

### [Blog 3 – Tutorial: Configuring a static website on Amazon S3](3.3-Blog3/)

Tóm tắt tài liệu chính thức cấu hình Static Website Hosting, Block Public Access và Bucket Policy — khớp phần frontend mục 5.4.

### [Blog 4 – Implement resource counters with Amazon DynamoDB](3.4-Blog4/)

Tóm tắt các cách đếm tài nguyên trên DynamoDB, tập trung atomic counter / `UpdateItem` — khớp logic tăng `clickCount` khi redirect.

### [Blog 5 – How to get notified on specific Lambda function error patterns using CloudWatch](3.5-Blog5/)

Tóm tắt cách nhận cảnh báo theo pattern lỗi trong log Lambda qua CloudWatch — liên hệ metric filter + alarm + SNS ở mục 5.5.
