---
title: "Serverless URL Shortener"
date: 2026-07-14
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Build a Serverless, Private URL Shortener

#### 1. Thông tin nguồn

| Hạng mục | Nội dung |
| --- | --- |
| Tiêu đề gốc | Build a Serverless, Private URL Shortener |
| Nguồn | [AWS Compute Blog](https://aws.amazon.com/blogs/compute/build-a-serverless-private-url-shortener/) |
| Chủ đề | URL shortener serverless, Lambda, API Gateway, S3 |

#### 2. Tóm tắt nội dung

Bài viết hướng dẫn xây một URL shortener “private” theo kiến trúc serverless: không tự quản lý server, tận dụng dịch vụ managed của AWS. Điểm then chốt của thiết kế mẫu là dùng **S3 Static Website Hosting như bộ máy redirect** — mỗi short link là một object (thường rất nhỏ) kèm metadata website redirect tới URL dài. Khi người dùng mở short URL, S3 trả HTTP redirect mà không cần code chạy ở bước redirect.

Phần tạo short link dùng trang admin HTML tĩnh trên S3; nút Shorten gọi **API Gateway → Lambda**. Lambda sinh mã ngắn ngẫu nhiên, ghi object vào S3 kèm metadata redirect. Có thể bọc thêm CloudFront (và CloudFormation mẫu trong bài) để có endpoint thống nhất / tối ưu phân phối.

#### 3. Nội dung chính

**3.1. S3 làm redirection engine**

- Bật website hosting trên bucket.
- Mỗi short code ≈ một object key; gắn `WebsiteRedirectLocation` (hoặc metadata tương đương) trỏ URL gốc.
- Request tới website endpoint được S3 trả redirect tự động.

**3.2. Tạo short link qua API**

- Frontend tĩnh gọi POST tới API Gateway.
- Lambda validate tham số, tạo key ngẫu nhiên (ví dụ ~5–7 ký tự), PutObject với metadata redirect.
- Trả short URL về cho người dùng.

**3.3. Thành phần phụ trợ**

- CloudFront (tuỳ chọn) cho CDN / custom domain.
- CloudFormation đóng gói S3, Lambda, API Gateway và các helper.

#### 4. Nhận xét (liên hệ dự án)

Bài viết đúng chủ đề URL shortener serverless, nhưng **khác thiết kế mình đã làm**:

| Hạng mục | Bài AWS Compute Blog | Workshop của mình |
| --- | --- | --- |
| Lưu mapping | Object S3 + redirect metadata | DynamoDB `url-shortener-links` |
| Redirect | S3 website redirect | Lambda trả **HTTP 302** |
| API vào | API Gateway | **Lambda Function URL** |
| Đếm click | Không phải trọng tâm | `clickCount` atomic khi redirect |

Cách AWS dùng S3 redirect rất gọn cho “chỉ rút gọn + chuyển hướng”. Mình chọn Lambda + DynamoDB vì cần **đếm click**, endpoint **stats**, và tách rõ frontend (S3) / backend (Function URL). Đọc bài này giúp hiểu trade-off: ít code hơn với S3 redirect, nhưng khó mở rộng nghiệp vụ (stats, điều kiện 404, giám sát lỗi trong cùng handler) bằng một lớp API tập trung như Function URL.
