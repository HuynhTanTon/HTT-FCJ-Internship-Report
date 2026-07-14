---
title: "Tổng quan kiến trúc"
date: 2026-07-14
weight: 1
chapter: false
pre: " 5.1. "
---

#### Mục tiêu

Phần này mô tả kiến trúc mình đã chọn cho URL Shortener serverless: các dịch vụ AWS tham gia, cách chúng kết nối, và luồng xử lý thực tế sau khi triển khai.

#### Luồng hoạt động

1. Người dùng mở trang web tĩnh trên **S3** (`index.html`), nhập link dài.
2. Frontend gọi `POST /` tới **Lambda Function URL** kèm `{ "url": "..." }`.
3. Lambda sinh mã ngắn 6 ký tự (`shortCode`), lưu vào **DynamoDB** (bảng `url-shortener-links`, partition key `shortCode`), trả về `shortUrl`.
4. Khi truy cập `shortUrl` (`GET /{shortCode}`), Lambda tra DynamoDB, tăng `clickCount` (atomic bằng `UpdateCommand`), rồi trả **HTTP 302** tới `originalUrl`.
5. `GET /stats/{shortCode}` xem số liệu (link gốc, số lượt click) mà không tăng đếm.

![overview](/images/5-Workshop/5.1-Tong-quan/architecture.png)

#### Lý do chọn kiến trúc này

+ **Lambda Function URL** cung cấp endpoint HTTPS public, đủ dùng cho API đơn giản, không cần API Gateway riêng.
+ **DynamoDB** phù hợp tra cứu key-value theo `shortCode`, on-demand, không cần quản trị.
+ **S3 Static Website Hosting** phục vụ frontend tĩnh với chi phí thấp và scale tự động.
