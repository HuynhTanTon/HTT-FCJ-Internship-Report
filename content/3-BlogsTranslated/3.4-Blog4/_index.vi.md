---
title: "DynamoDB counters"
date: 2026-07-14
weight: 4
chapter: false
pre: " <b> 3.4. </b> "
---

# Implement resource counters with Amazon DynamoDB

#### 1. Thông tin nguồn

| Hạng mục | Nội dung |
| --- | --- |
| Tiêu đề gốc | Implement resource counters with Amazon DynamoDB |
| Nguồn | [AWS Database Blog](https://aws.amazon.com/blogs/database/implement-resource-counters-with-amazon-dynamodb/) |
| Chủ đề | Atomic counter, `UpdateItem`, ConditionExpression, độ chính xác khi đồng thời |

#### 2. Tóm tắt nội dung

Bài viết phân tích bài toán **đếm tài nguyên** trên DynamoDB (vote, tồn kho, vé…) khi nhiều process cập nhật cùng lúc. Tác giả so sánh nhiều cách tiếp cận về độ chính xác, chi phí và độ phức tạp — từ **atomic counters** đơn giản bằng `UpdateItem`/`ADD`, thêm ConditionExpression để không vượt ngưỡng, đến optimistic concurrency, transaction có client request token, đếm bằng item collection / set. Điểm then chốt: phải tính tới lỗi 500-series (không chắc update đã apply hay chưa) và chiến lược retry để tránh over/undercount.

#### 3. Nội dung chính

**3.1. Atomic counters**

- Một `UpdateItem` tăng/giảm counter; DynamoDB serialize thao tác trên item.
- Có thể kèm condition (ví dụ không để counter < 0).
- Rẻ và đơn giản; độ chính xác thấp hơn các pattern transaction khi gặp failure/retry phức tạp — phù hợp khi chấp nhận xấp xỉ hoặc khi điều kiện đơn giản là đủ.

**3.2. Condition và ngưỡng**

ConditionExpression giúp từ chối update khi điều kiện không thỏa (tránh “âm kho”, tránh tạo/cập nhật sai trạng thái).

**3.3. Các hướng nâng cao**

OCC, TransactWriteItems + client request token, marker item… dành cho bài toán cần độ chính xác / idempotency cao hơn atomic counter thuần.

#### 4. Nhận xét (liên hệ dự án)

Khớp trực tiếp với `clickCount` trong handler redirect của mình:

- Dùng `UpdateCommand` / atomic increment thay vì Get rồi Put (giảm race).
- `ConditionExpression: attribute_exists(shortCode)` → mã không tồn tại thì fail có kiểm soát (404), không “đẻ” item mới.
- Phạm vi lab: atomic counter là đủ để demo số lượt click; bài blog giúp hiểu vì sao pattern này đúng hướng và khi nào cần transaction nếu yêu cầu đếm cực chặt (ví dụ inventory bán hàng).
