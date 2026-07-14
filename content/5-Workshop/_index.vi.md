---
title: "Workshop"
date: 2026-07-14
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Serverless URL Shortener trên AWS

#### Tổng quan

Mục 5 ghi lại quá trình mình triển khai thực nghiệm ứng dụng **rút gọn đường link (URL Shortener)** chạy hoàn toàn **serverless** trên AWS. Nội dung trình bày theo hướng báo cáo kỹ thuật: mô tả mục tiêu, kiến trúc đã chọn, các bước thực hiện và kết quả đạt được.

Ứng dụng gồm ba lớp: giao diện web tĩnh trên **Amazon S3**, logic nghiệp vụ trên **AWS Lambda (Function URL)**, và lưu trữ trên **Amazon DynamoDB**. Toàn bộ hệ thống triển khai tại region **ap-southeast-1 (Singapore)**, không quản lý server và không dùng API Gateway riêng.

#### Phạm vi đã triển khai

- **Frontend**: bucket S3 `url-shortener-frontend-forward` bật Static Website Hosting, phục vụ `index.html` / `config.js`.
- **Backend**: hàm Lambda `url-shortener-backend` qua Function URL (`POST /` tạo mã, `GET /{shortCode}` redirect 302, `GET /stats/{shortCode}` xem số liệu).
- **Dữ liệu**: bảng DynamoDB `url-shortener-links` (partition key `shortCode`) lưu `originalUrl`, `clickCount`, `createdAt`; capacity mode on-demand.
- **Giám sát (nâng cao)**: đếm click atomic khi redirect; Metric filter + CloudWatch Alarm + SNS khi log có `[ERROR]`.

#### Cấu trúc mục 5

1. [Tổng quan kiến trúc](5.1-Tong-quan/) — luồng hoạt động end-to-end và lý do chọn S3 + Lambda Function URL + DynamoDB.
2. [Chuẩn bị](5.2-Chuan-bi/) — tên tài nguyên cố định và IAM Role/policy đã tạo cho Lambda.
3. [Triển khai Backend](5.3-Backend/) — tạo Lambda, Function URL và kiểm thử API / DynamoDB.
4. [Triển khai Frontend](5.4-Frontend/) — S3 Static Website, Bucket Policy, upload frontend và test end-to-end.
5. [Nâng cao (làm thêm)](5.5-Nang-cao/) — `clickCount` atomic và cảnh báo lỗi CloudWatch / SNS.
6. [Dọn dẹp tài nguyên](5.6-Don-dep/) — danh sách tài nguyên cần thu hồi sau demo để tránh phát sinh chi phí.
