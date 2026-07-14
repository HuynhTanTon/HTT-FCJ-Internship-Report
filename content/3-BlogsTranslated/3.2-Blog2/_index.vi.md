---
title: "Lambda Function URLs"
date: 2026-07-14
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Announcing AWS Lambda Function URLs

#### 1. Thông tin nguồn

| Hạng mục | Nội dung |
| --- | --- |
| Tiêu đề gốc | Announcing AWS Lambda Function URLs: Built-in HTTPS Endpoints for Single-Function Microservices |
| Nguồn | [AWS News Blog](https://aws.amazon.com/blogs/aws/announcing-aws-lambda-function-urls-built-in-https-endpoints-for-single-function-microservices/) |
| Chủ đề | Lambda Function URL, HTTPS endpoint, CORS, so sánh API Gateway |

#### 2. Tóm tắt nội dung

AWS công bố **Lambda Function URLs**: gắn endpoint HTTPS sẵn có cho một hàm Lambda, tuỳ chọn cấu hình CORS, không bắt buộc thêm API Gateway hay ALB. Endpoint gắn với alias/`$LATEST`, hỗ trợ tạo qua console, SDK, CloudFormation / SAM / CDK. Auth mặc định gắn với IAM; có thể chọn `NONE` cho endpoint công khai (kèm cập nhật resource-based policy). Không tính phí riêng ngoài chi phí invoke Lambda thông thường.

#### 3. Nội dung chính

**3.1. Khi nào phù hợp Function URL**

Phù hợp microservice **một hàm** cần endpoint công khai mà **không cần** khả năng nâng cao của API Gateway: request validation, throttling tinh, custom authorizer, custom domain, usage plan, caching… Ví dụ trong bài: webhook, form validator, inference đơn giản, R&D nhanh trong console.

**3.2. Khi nên dùng API Gateway**

Khi cần các tính năng quản trị / bảo mật API ở mức nền tảng (API key, stage, WAF gắn sẵn theo mô hình API, v.v.), Function URL không thay thế trọn vẹn API Gateway.

**3.3. CORS và truy cập**

Function URL hỗ trợ cấu hình CORS native. Đây là điểm quan trọng khi frontend ở domain khác gọi API (đúng tình huống S3 website endpoint gọi Function URL).

#### 4. Nhận xét (liên hệ dự án)

Đây là bài giải thích **đúng cơ chế backend** mình chọn cho URL Shortener: một hàm `url-shortener-backend` phục vụ `POST /`, `GET /{code}`, `GET /stats/...` qua Function URL, Auth `NONE`, bật CORS cho frontend S3.

So với bài Compute Blog (URL shortener dùng API Gateway), Function URL giúp lab **giảm số tài nguyên** và vẫn đủ HTTPS. Trade-off mình chấp nhận: chưa có custom domain, throttling nâng cao hay usage plan — phù hợp phạm vi thực tập; production có thể cân nhắc CloudFront / API Gateway phía trước như gợi ý của AWS khi nhu cầu tăng.
