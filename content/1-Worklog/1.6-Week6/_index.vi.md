---
title: "Worklog Tuần 6"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

**Thời gian:** 25/05/2026 – 31/05/2026

### Mục tiêu tuần 6:

* Xây dựng ứng dụng serverless với Lambda, API Gateway và Step Functions.
* Hiểu kiến trúc event-driven và mô hình tính phí theo lượt gọi.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | Lab 1: Viết Lambda (Python) tự động xóa EC2 snapshot cũ hơn 30 ngày; EventBridge chạy lúc 2:00 AM. | 25/05/2026 | 25/05/2026 | <https://000022.awsstudygroup.com/><br><https://000066.awsstudygroup.com/> |
| 3 | Lab 2: Xây dựng REST API Book Store — API Gateway + Lambda + DynamoDB (CRUD, JSON status code). | 26/05/2026 | 27/05/2026 | <https://000078.awsstudygroup.com/><br><https://000066.awsstudygroup.com/> |
| 4 | Tiếp tục Book Store backend; tích hợp S3 nếu cần; kiểm tra response API. | 28/05/2026 | 28/05/2026 | <https://000078.awsstudygroup.com/><br><https://000079.awsstudygroup.com/> |
| 5 | Lab 3: Step Functions — ValidateOrder → ProcessPayment → UpdateInventory → SendNotification. | 29/05/2026 | 29/05/2026 | <https://000047.awsstudygroup.com/> |
| 6 | Kiểm tra error handling / retry; tối ưu Lambda timeout (3s → 30s) và giảm cold start. | 30/05/2026 | 30/05/2026 | <https://000047.awsstudygroup.com/><br><https://000077.awsstudygroup.com/> |

### Kết quả đạt được tuần 6:

* Hiểu event-driven architecture và lợi ích serverless.
* Xây dựng REST API Book Store với API Gateway + Lambda + DynamoDB.
* Thiết kế workflow nhiều bước với Step Functions (error handling, retry).

### Khó khăn và cách giải quyết:

* Lambda timeout với mặc định 3 giây → tăng timeout lên 30 giây và tối ưu code giảm cold start.

### Kế hoạch tuần tiếp theo:

* Học Infrastructure as Code với CloudFormation, CDK và CI/CD pipeline.
