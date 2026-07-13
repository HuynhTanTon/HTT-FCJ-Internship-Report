---
title: "Worklog Tuần 7"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

**Thời gian:** 01/06/2026 – 07/06/2026

### Mục tiêu tuần 7:

* Thực hành Infrastructure as Code với CloudFormation và CDK.
* Xây dựng CI/CD pipeline và truy cập từ xa bằng Systems Manager Session Manager.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | Lab 1: Viết CloudFormation YAML deploy VPC, 2 Subnet, Security Group, EC2 bằng một lệnh CLI. | 01/06/2026 | 01/06/2026 | <https://000037.awsstudygroup.com/><br><https://000102.awsstudygroup.com/> |
| 3 | Lab 2: Khởi tạo CDK app (TypeScript) với S3 + Lambda; chạy `cdk bootstrap`, `cdk synth`, `cdk deploy`. | 02/06/2026 | 02/06/2026 | <https://000038.awsstudygroup.com/><br><https://000076.awsstudygroup.com/> |
| 4 | Lab 3: Xây dựng CodePipeline — Source (CodeCommit) → Build (CodeBuild) → Deploy (CloudFormation). | 03/06/2026 | 04/06/2026 | <https://000023.awsstudygroup.com/><br><https://000084.awsstudygroup.com/> |
| 5 | Lab 4: Kết nối EC2 không public IP / không mở port 22 bằng SSM Session Manager. | 05/06/2026 | 05/06/2026 | <https://000058.awsstudygroup.com/><br><https://000031.awsstudygroup.com/> |
| 6 | Ôn giá trị IaC (version control, tái sử dụng, tự động hóa); kiểm tra pipeline sau mỗi lần push. | 06/06/2026 | 06/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 7:

* Deploy hạ tầng bằng CloudFormation và CDK.
* Xây dựng CI/CD pipeline end-to-end.
* Truy cập EC2 an toàn qua Session Manager không cần SSH.

### Khó khăn và cách giải quyết:

* CDK deploy lần đầu thất bại do chưa bootstrap → chạy `cdk bootstrap` rồi deploy lại.

### Kế hoạch tuần tiếp theo:

* Học Container Services: Docker, Amazon ECS và Fargate.
