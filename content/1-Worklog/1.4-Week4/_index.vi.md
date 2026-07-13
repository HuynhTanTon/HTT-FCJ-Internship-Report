---
title: "Worklog Tuần 4"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

**Thời gian:** 11/05/2026 – 17/05/2026

### Mục tiêu tuần 4:

* Khởi chạy và quản lý Amazon EC2.
* Cấu hình Auto Scaling và giám sát với CloudWatch.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | Lab 1: Khởi chạy EC2 (Amazon Linux 2), cài Apache, mở port 80/443, truy cập bằng Public IP. | 11/05/2026 | 11/05/2026 | <https://000004.awsstudygroup.com/> |
| 3 | Tìm hiểu AMI, Key Pair, Elastic IP; cấu hình Security Group SSH an toàn (IP cá nhân). | 12/05/2026 | 12/05/2026 | <https://000004.awsstudygroup.com/> |
| 4 | Lab 2: Tạo Launch Template và Auto Scaling Group (min=1, max=3), scaling theo CPU. | 13/05/2026 | 13/05/2026 | <https://000006.awsstudygroup.com/> |
| 5 | Lab 3: Tạo CloudWatch Dashboard (CPU, Network, StatusCheck); Alarm + SNS khi CPU > 70%. | 14/05/2026 | 14/05/2026 | <https://000036.awsstudygroup.com/><br><https://000008.awsstudygroup.com/> |
| 6 | Kiểm tra Auto Scaling khi tải cao; ôn vòng đời EC2 (launch/stop/start/terminate). | 15/05/2026 | 15/05/2026 | <https://000006.awsstudygroup.com/><br><https://000004.awsstudygroup.com/> |

### Kết quả đạt được tuần 4:

* Thành thạo vòng đời EC2 và triển khai web server trên cloud.
* Cấu hình Auto Scaling theo CPU utilization.
* Giám sát và cảnh báo chủ động bằng CloudWatch + SNS.

### Khó khăn và cách giải quyết:

* Không SSH được do Security Group chưa mở port 22 → thêm inbound SSH với IP cá nhân (không dùng 0.0.0.0/0).

### Kế hoạch tuần tiếp theo:

* Học lưu trữ: Amazon S3, RDS và DynamoDB.
