---
title: "Worklog Tuần 3"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

**Thời gian:** 04/05/2026 – 06/05/2026

### Mục tiêu tuần 3:

* Thiết kế và triển khai hạ tầng mạng với Amazon VPC.
* Cấu hình Public/Private Subnet, IGW, NAT Gateway, Security Groups và NACL.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | Tìm hiểu kiến trúc VPC (CIDR, Subnet, Route Table, IGW). Lab 1: Triển khai VPC 10.0.0.0/16, tạo Public & Private Subnet, cấu hình Internet Gateway. | 04/05/2026 | 04/05/2026 | <https://000003.awsstudygroup.com/> |
| 3 | Cấu hình NAT Gateway cho Private Subnet; phân biệt Security Group (stateful) và NACL (stateless). | 05/05/2026 | 05/05/2026 | <https://000003.awsstudygroup.com/> |
| 4 | Lab 2: Networking Workshop — multi-tier (web public, DB private); debug Route Table / NAT; kiểm tra private subnet ra internet qua NAT Gateway. | 06/05/2026 | 06/05/2026 | <https://000092.awsstudygroup.com/><br><https://000003.awsstudygroup.com/> |

### Kết quả đạt được tuần 3:

* Triển khai VPC với public/private subnet, IGW và NAT Gateway.
* Hiểu luồng traffic qua Route Table.
* Phân biệt Security Group và Network ACL.

### Khó khăn và cách giải quyết:

* NAT Gateway không hoạt động do thiếu route trong Route Table của private subnet → tự debug Route Table theo tài liệu lab.

### Kế hoạch tuần tiếp theo:

* Tìm hiểu Amazon EC2 — khởi chạy máy chủ ảo và cấu hình Auto Scaling.
