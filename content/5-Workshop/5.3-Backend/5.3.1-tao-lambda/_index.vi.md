---
title: "Tạo Lambda function & Function URL"
date: 2026-07-14
weight: 1
chapter: false
pre: " 5.3.1. "
---

Mình tạo hàm Lambda với các cấu hình sau:

1. **Create function** → Author from scratch
   - Function name: `url-shortener-backend`
   - Runtime: **Node.js 20.x**
   - Execution role: `url-shortener-lambda-role`

2. Trong tab **Code**, thay nội dung `index.mjs` bằng code xử lý URL shortener (dùng AWS SDK v3 có sẵn trong runtime Lambda — `@aws-sdk/client-dynamodb`, `@aws-sdk/lib-dynamodb`, không cần `npm install` trên console).

3. **Configuration → Environment variables**:
   - `TABLE_NAME` = `url-shortener-links`

4. Bật **Function URL**:
   - Auth type: `NONE` (API công khai cho rút gọn link)
   - CORS: `Access-Control-Allow-Origin: *`, methods `GET, POST`

![lambda](/images/5-Workshop/5.3-Backend/create-lambda.png)

Function URL đã tạo (dạng `https://xxxx.lambda-url.ap-southeast-1.on.aws/`) được dùng để cấu hình frontend ở bước tiếp theo.
