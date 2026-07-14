---
title: "Test API"
date: 2026-07-14
weight: 2
chapter: false
pre: " 5.3.2. "
---

#### Kiểm thử tạo link ngắn

Mình gọi API tạo short link bằng `curl` (hoặc qua giao diện sau khi có frontend):

```bash
curl -X POST https://<function-url>/ \
  -H "Content-Type: application/json" \
  -d '{"url":"https://www.google.com"}'
```

Response nhận được có dạng:

```json
{ "shortCode": "aZ3kT9", "shortUrl": "https://<function-url>/aZ3kT9", "originalUrl": "https://www.google.com" }
```

![Kết quả tạo link ngắn trên giao diện](/images/5-Workshop/5.3-Backend/frontend-shorten-result.png)

#### Kiểm thử redirect

Khi mở short URL trên trình duyệt, hệ thống trả **302** và chuyển về URL gốc. Mình xác nhận status bằng PowerShell:

```powershell
Invoke-WebRequest -Uri "https://<function-url>/<shortCode>" -MaximumRedirection 0
```

![Test redirect HTTP 302](/images/5-Workshop/5.3-Backend/test-redirect-302.png)

#### Kiểm thử thống kê

```bash
curl https://<function-url>/stats/<shortCode>
```

```json
{ "shortCode": "aZ3kT9", "originalUrl": "https://www.google.com", "clickCount": 1, "createdAt": "..." }
```

#### Kiểm tra dữ liệu trên DynamoDB

Trong console DynamoDB → table `url-shortener-links` → **Explore table items**, mình xác nhận các item đã được tạo/cập nhật đúng (`shortCode`, `originalUrl`, `clickCount`, `createdAt`).

![dynamodb items](/images/5-Workshop/5.3-Backend/dynamodb-items.png)
