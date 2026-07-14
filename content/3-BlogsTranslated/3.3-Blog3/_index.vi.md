---
title: "S3 Static Website"
date: 2026-07-14
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Tutorial: Configuring a static website on Amazon S3

#### 1. Thông tin nguồn

| Hạng mục | Nội dung |
| --- | --- |
| Tiêu đề gốc | Tutorial: Configuring a static website on Amazon S3 |
| Nguồn | [Amazon S3 User Guide](https://docs.aws.amazon.com/AmazonS3/latest/userguide/HostingWebsiteOnS3Setup.html) |
| Chủ đề | Static Website Hosting, Block Public Access, Bucket Policy, website endpoint |

#### 2. Tóm tắt nội dung

Tài liệu chính thức hướng dẫn từng bước biến một bucket S3 thành website tĩnh: tạo bucket, bật Static website hosting và chỉ định `index.html`, chỉnh Block Public Access, thêm Bucket Policy public `GetObject`, upload nội dung, rồi test bằng **website endpoint**. AWS nhấn mạnh S3 website endpoint mặc định là **HTTP**; production nên cân nhắc CloudFront (+ HTTPS) và Origin Access Control thay vì để bucket public nếu muốn giữ Block Public Access bật.

#### 3. Nội dung chính

**3.1. Bật Static website hosting** — Properties → Static website hosting → Enabled; Index document = `index.html` (phân biệt hoa thường).

**3.2. Quyền công khai** — tắt/chỉnh Block Public Access theo mức cần thiết; gắn policy `Principal: "*"` + `s3:GetObject` trên `arn:aws:s3:::bucket/*`.

**3.3. Kiểm thử** — dùng Website endpoint (không nhầm với REST endpoint của S3). Upload sai Content-Type hoặc thiếu policy → 403 / Access Denied.

**3.4. Hạn chế HTTP** — docs khuyến nghị CloudFront khi cần HTTPS, custom domain, header bảo mật tốt hơn.

#### 4. Nhận xét (liên hệ dự án)

Đây đúng checklist mình đã làm ở mục **5.4**:

1. Bucket `url-shortener-frontend-forward`
2. Enable Static website hosting
3. Bucket Policy public read `GetObject`
4. Upload `index.html`, `config.js`, ảnh nền
5. Test e2e trên website endpoint

Điểm học thêm từ docs: ranh giới rõ giữa **website endpoint** và **REST endpoint**, và giới hạn HTTP — phù hợp giải thích hạn chế lab trong phần dọn dẹp / hướng cải thiện (CloudFront + ACM).
