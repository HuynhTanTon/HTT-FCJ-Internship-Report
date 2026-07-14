---
title: "Dọn dẹp tài nguyên"
date: 2026-07-14
weight: 6
chapter: false
pre: " 5.6. "
---

#### Tổng kết

Sau khi hoàn thành triển khai, mình đã có ứng dụng rút gọn URL serverless trên AWS gồm: **S3** (frontend), **Lambda Function URL** (backend), **DynamoDB** (lưu trữ), và giám sát lỗi qua **CloudWatch** / SNS. Phần này ghi các tài nguyên cần thu hồi sau demo để tránh phát sinh chi phí.

#### Danh sách tài nguyên cần dọn

1. Lambda function `url-shortener-backend` (kèm Function URL).
2. DynamoDB table `url-shortener-links`.
3. Toàn bộ object trong S3 bucket `url-shortener-frontend-forward`, rồi xoá bucket.
4. IAM Role gắn với Lambda (ví dụ role đã xoá `url-shortener-backend-role-...` hoặc `url-shortener-lambda-role`) và policy DynamoDB kèm theo.
5. CloudWatch Alarm `url-shortener-error-alarm`, Metric filter, và Log group `/aws/lambda/url-shortener-backend`.
6. SNS topic đã dùng để nhận cảnh báo.

![cleanup](/images/5-Workshop/5.6-Don-dep/cleanup.png)
