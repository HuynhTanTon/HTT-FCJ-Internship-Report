---
title: "Worklog Tuần 2"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

**Thời gian:** 27/04/2026 – 29/04/2026

### Mục tiêu tuần 2:

* Quản lý danh tính và quyền truy cập với AWS IAM.
* Áp dụng Least Privilege, MFA và IAM Role cho EC2.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | Tìm hiểu mô hình IAM (User, Group, Role, Policy), Least Privilege, MFA. Lab 1: Tạo IAM Users, Groups (Dev, Ops), gán Managed Policies, kiểm tra bằng Policy Simulator. | 27/04/2026 | 27/04/2026 | <https://000002.awsstudygroup.com/> |
| 3 | Tìm hiểu IAM Permission Boundaries và cách giới hạn quyền người dùng. | 28/04/2026 | 28/04/2026 | <https://000030.awsstudygroup.com/> |
| 4 | Lab 2: Tạo IAM Role cho EC2 (Instance Profile) truy cập S3 không lưu Access Key; gắn Role, kiểm tra quyền; ôn IAM Role & Condition. | 29/04/2026 | 29/04/2026 | <https://000048.awsstudygroup.com/><br><https://000044.awsstudygroup.com/> |

### Kết quả đạt được tuần 2:

* Hiểu sâu User, Group, Role, Policy và nguyên tắc Least Privilege.
* Tạo IAM Users/Groups và kiểm tra quyền bằng Policy Simulator.
* Cấu hình IAM Role cho EC2 truy cập S3 không cần Access Key.

### Khó khăn và cách giải quyết:

* Viết IAM Policy JSON dễ lỗi cú pháp → dùng IAM Policy Editor trên Console và tài liệu AWS.

### Kế hoạch tuần tiếp theo:

* Nghiên cứu Amazon VPC — xây dựng hạ tầng mạng riêng ảo trên AWS.
