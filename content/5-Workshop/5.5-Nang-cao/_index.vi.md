---
title: "Nâng cao (làm thêm)"
date: 2026-07-14
weight: 5
chapter: false
pre: " 5.5. "
---

#### Đếm lượt click (`clickCount`)

Trong luồng redirect (`GET /{shortCode}`), code dùng `UpdateCommand` để tăng `clickCount` **atomic**, kèm `ConditionExpression: attribute_exists(shortCode)` để trả 404 khi mã không tồn tại. IAM policy đã gồm `dynamodb:UpdateItem` (xem mục 5.2).

#### Cảnh báo lỗi qua CloudWatch

Mình đã cấu hình giám sát lỗi cho Lambda:

1. Metric filter trên log group `/aws/lambda/url-shortener-backend` với pattern `"[ERROR]"`, metric `URLShortenerErrorCount` (namespace `URLShortener`).
2. CloudWatch Alarm `url-shortener-error-alarm` trên metric đó (ngưỡng theo cấu hình alarm — khi có đủ datapoint sẽ chuyển OK / In alarm).
3. SNS topic subscribe email để nhận cảnh báo khi alarm kích hoạt.

![cloudwatch alarm](/images/5-Workshop/5.5-Nang-cao/alarm.png)
