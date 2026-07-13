---
title: "Worklog Tuần 5"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

**Thời gian:** 18/05/2026 – 20/05/2026

### Mục tiêu tuần 5:

* Thực hành lưu trữ đám mây: S3, RDS, DynamoDB, ElastiCache.
* Chọn giải pháp lưu trữ phù hợp theo use case, chi phí và hiệu năng.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | Lab 1: Static Website Hosting với S3 — upload HTML/CSS/JS, bật hosting, Bucket Policy public read. Lab 2: Triển khai RDS MySQL trong Private Subnet, Multi-AZ; kết nối từ EC2 và CRUD. | 18/05/2026 | 18/05/2026 | <https://000057.awsstudygroup.com/><br><https://000005.awsstudygroup.com/> |
| 3 | Lab 3: Tạo DynamoDB table (Partition/Sort Key); PutItem, GetItem, Query, Scan; so sánh GSI. | 19/05/2026 | 19/05/2026 | <https://000060.awsstudygroup.com/><br><https://000039.awsstudygroup.com/> |
| 4 | Lab 4: Triển khai ElastiCache Redis, cache query RDS (latency ~50ms → ~2ms). Tổng hợp trade-off S3 / RDS / DynamoDB / ElastiCache; kiểm tra Security Group RDS ← EC2. | 20/05/2026 | 20/05/2026 | <https://000061.awsstudygroup.com/><br><https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 5:

* Host website tĩnh trên S3 thành công.
* Triển khai RDS Multi-AZ và DynamoDB với GSI.
* Giảm latency ~25 lần nhờ ElastiCache Redis.

### Khó khăn và cách giải quyết:

* EC2 không kết nối RDS do Security Group RDS chưa cho phép inbound từ SG của EC2 → sửa inbound rule.

### Kế hoạch tuần tiếp theo:

* Tìm hiểu Serverless với AWS Lambda và API Gateway.
