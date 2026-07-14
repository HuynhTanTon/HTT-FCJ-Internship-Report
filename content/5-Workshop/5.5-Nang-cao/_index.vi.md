---
title: "Nâng cao (làm thêm)"
date: 2026-07-14
weight: 5
chapter: false
pre: " 5.5. "
---

#### Mục tiêu phần nâng cao

Sau khi luồng rút gọn / redirect đã chạy, mình bổ sung hai hạng mục gần với vận hành thực tế hơn: **đếm click an toàn khi đồng thời** và **cảnh báo khi Lambda ghi log lỗi**.

#### Đếm lượt click (`clickCount`)

Ở handler redirect (`GET /{shortCode}`), thay vì `GetItem` rồi `PutItem` riêng (dễ race condition), mình dùng `UpdateCommand` để tăng `clickCount` **atomic** trên DynamoDB:

- `SET clickCount = if_not_exists(clickCount, :zero) + :inc`
- `ConditionExpression: attribute_exists(shortCode)` — mã không tồn tại → ConditionalCheckFailed → **404**, không “tạo nhầm” item mới.

Nhờ đó nhiều request redirect cùng lúc vẫn tăng đếm đúng hơn so với read-modify-write thủ công. Policy IAM đã gồm `dynamodb:UpdateItem` (mục 5.2).

#### Cảnh báo lỗi qua CloudWatch + SNS

Chuỗi giám sát mình cấu hình:

1. **Metric filter** trên log group `/aws/lambda/url-shortener-backend`  
   - Pattern: `"[ERROR]"`  
   - Metric: `URLShortenerErrorCount` (namespace `URLShortener`)
2. **Alarm** `url-shortener-error-alarm` theo dõi metric trên (ngưỡng theo cấu hình alarm, cửa sổ ~5 phút).
3. **SNS** subscribe email — xác nhận subscription trước khi nhận được mail cảnh báo thật.

![cloudwatch alarm](/images/5-Workshop/5.5-Nang-cao/alarm.png)

#### Giải thích trạng thái Insufficient data

Trên ảnh alarm thường thấy **Insufficient data** khi chưa có datapoint (chưa có log khớp `"[ERROR]"` trong cửa sổ đánh giá). Điều này **không có nghĩa alarm hỏng** — chỉ là hệ thống chưa nhận tín hiệu lỗi. Khi Lambda log `[ERROR]` đủ điều kiện, metric tăng và alarm có thể chuyển **In alarm** rồi gửi SNS.

#### Giá trị mang lại

- `clickCount` biến demo shortener thành có “số liệu sử dụng” tối thiểu.
- Metric filter + Alarm + SNS cho thấy vòng **quan sát → cảnh báo**, dù lab chưa dựng dashboard Grafana phức tạp.
