---
title: "Tổng quan kiến trúc"
date: 2026-07-14
weight: 1
chapter: false
pre: " 5.1. "
---

#### Mục tiêu phần này

Trình bày kiến trúc thực tế mình đã triển khai: các thành phần AWS, cách chúng gọi nhau, và ý nghĩa từng API trên Function URL.

#### Sơ đồ kiến trúc logic

```text
[ Trình duyệt ]
      │
      │ 1) mở website endpoint
      ▼
[ S3 Static Website ]
  index.html + config.js
      │
      │ 2) fetch POST /  { "url": "..." }
      ▼
[ Lambda Function URL ]  url-shortener-backend
      │
      │ 3) PutItem / UpdateItem / GetItem
      ▼
[ DynamoDB ]  url-shortener-links
   PK: shortCode (S)
```

Khi người dùng bấm link ngắn, trình duyệt gọi thẳng Function URL (`GET /{shortCode}`); Lambda trả **302** kèm header `Location` trỏ về `originalUrl`. Frontend S3 không tham gia bước redirect này.

#### Luồng API đã thiết kế

| Method & path | Mục đích | Ghi DynamoDB | Ảnh hưởng click |
| ------------- | -------- | ------------ | --------------- |
| `POST /` | Tạo short link | `PutItem` | Không |
| `GET /{shortCode}` | Redirect về URL gốc | `UpdateItem` (tăng `clickCount`) | Có |
| `GET /stats/{shortCode}` | Xem số liệu | đọc (sau UpdateCondition/Get) | Không |

Luồng tạo link:

1. Người dùng mở S3 website, dán URL dài.
2. `index.html` đọc Function URL từ `config.js`, gọi `POST /` với JSON `{ "url": "..." }`.
3. Lambda sinh `shortCode` 6 ký tự, lưu item vào DynamoDB, trả `{ shortCode, shortUrl, originalUrl }`.

Luồng mở link ngắn:

1. Client gọi `GET /{shortCode}` trên Function URL.
2. Lambda cập nhật `clickCount` atomic nếu `shortCode` tồn tại; nếu không → 404.
3. Trả **302** tới `originalUrl`.

#### Vì sao chọn Function URL thay vì API Gateway

- Lab chỉ cần một API HTTPS đơn giản, Auth type `NONE` + CORS là đủ.
- Giảm số tài nguyên phải cấu hình và dọn dẹp (không thêm stage, method, integration của API Gateway).
- Chi phí và độ phức tạp thấp hơn cho phạm vi demo nội bộ / báo cáo thực tập.

Đổi lại, Function URL ít tính năng quản trị hơn API Gateway (throttle nâng cao, API key, usage plan…). Với URL shortener lab này thì trade-off chấp nhận được.

#### Vì sao chọn DynamoDB

Bài toán cốt lõi là **tra cứu theo khóa** `shortCode` → `originalUrl`. DynamoDB on-demand phù hợp: không phải dự phòng capacity, độ trễ đọc/ghi thấp, và không cần vận hành instance như RDS.

#### Kết quả kiến trúc mang lại

Sau khi dựng đủ ba lớp, mình có một đường đi khép kín: tạo link trên UI S3 → lưu DynamoDB → mở short URL qua Lambda → redirect + đếm click → xem stats / quan sát dữ liệu trên console.
