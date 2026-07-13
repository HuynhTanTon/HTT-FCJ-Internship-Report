---
title: "Worklog Tuần 8"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

**Thời gian:** 08/06/2026 – 10/06/2026

### Mục tiêu tuần 8:

* Containerize ứng dụng với Docker và triển khai trên Amazon ECS / Fargate.
* Hiểu sự khác biệt giữa EC2 launch type và Fargate.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | Lab 1: Viết Dockerfile cho ứng dụng Node.js, build image local, push lên Amazon ECR. | 08/06/2026 | 08/06/2026 | <https://000015.awsstudygroup.com/> |
| 3 | Lab 2: Tạo ECS Cluster, Task Definition (image từ ECR), ECS Service 2 tasks + ALB; cấu hình resource limits, environment variables; xử lý IAM Role pull ECR. | 09/06/2026 | 09/06/2026 | <https://000016.awsstudygroup.com/><br><https://000017.awsstudygroup.com/> |
| 4 | Lab 3: Chuyển sang launch type Fargate — không quản lý EC2, tính phí theo vCPU/memory; so sánh EC2 launch type vs Fargate và kiểm tra ổn định. | 10/06/2026 | 10/06/2026 | <https://000067.awsstudygroup.com/><br><https://000016.awsstudygroup.com/> |

### Kết quả đạt được tuần 8:

* Nắm quy trình Dockerfile → build → ECR → ECS.
* Triển khai ECS Service với ALB và 2 tasks.
* Chạy ứng dụng trên Fargate không cần quản lý server.

### Khó khăn và cách giải quyết:

* ECS Service fail vì Task Execution Role thiếu quyền pull ECR → gắn `AmazonEC2ContainerRegistryReadOnly`.

### Kế hoạch tuần tiếp theo:

* Học Amazon EKS — triển khai và quản lý Kubernetes cluster trên AWS.
