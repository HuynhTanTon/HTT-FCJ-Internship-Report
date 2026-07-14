---
title: "Test end-to-end"
date: 2026-07-14
weight: 4
chapter: false
pre: " 5.4.4. "
---

#### Kịch bản đã chạy trên trình duyệt

1. Mở website endpoint:  
   `http://url-shortener-frontend-forward.s3-website-ap-southeast-1.amazonaws.com`
2. Dán một URL dài (ví dụ trang báo cáo GitHub Pages / `https://www.google.com`).
3. Bấm **Tạo link ngắn** → UI hiển thị `shortUrl` dạng Function URL + `shortCode`.
4. Mở `shortUrl` → trình duyệt chuyển về đúng link gốc.
5. (Tuỳ chọn) gọi `/stats/{shortCode}` hoặc xem lại `clickCount` trên DynamoDB.

![e2e test](/images/5-Workshop/5.4-Frontend/test-result.png)

#### Kiểm tra CORS trên DevTools

Vì origin của S3 website **khác** origin của Lambda Function URL, trình duyệt bắt buộc preflight:

- Request `OPTIONS` (preflight) → 200
- Request `POST`/`fetch` tạo link → 200 + response JSON

Trên tab **Network** (tick **Preserve log**), mình thấy các request tới Function URL gồm preflight và fetch thành công — chứng tỏ CORS trên Function URL và header từ Lambda đã khớp.

![cors network](/images/5-Workshop/5.4-Frontend/cors-network.png)

#### Ý nghĩa bài test này

Đây là lần đầu toàn chuỗi **S3 → Lambda → DynamoDB → redirect** chạy trên trình duyệt thật, không chỉ test curl backend. Nếu chỉ gọi API bằng curl mà không qua UI, sẽ bỏ sót lỗi CORS — lỗi rất hay gặp khi ghép static frontend với Function URL.
