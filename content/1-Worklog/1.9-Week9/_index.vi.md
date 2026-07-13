---
title: "Worklog Tuần 9"
date: 2024-01-01
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

**Thời gian:** 15/06/2026 – 21/06/2026

### Mục tiêu tuần 9:

* Tạo và quản lý Amazon EKS cluster.
* Thực hành Kubernetes: Pods, Deployments, Services, ConfigMaps, Helm.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | Tìm hiểu kiến trúc Kubernetes: Control Plane, Worker Nodes, etcd; cài `eksctl` và `kubectl`. | 15/06/2026 | 15/06/2026 | <https://000126.awsstudygroup.com/><br><https://000065.awsstudygroup.com/> |
| 3 | Lab 1: Tạo EKS Cluster bằng `eksctl`, cấu hình kubectl, kiểm tra node group (`kubectl get nodes`). | 16/06/2026 | 17/06/2026 | <https://000062.awsstudygroup.com/><br><https://000065.awsstudygroup.com/> |
| 4 | Thực hành Deployment / Service (ClusterIP, NodePort, LoadBalancer); theo dõi vòng đời Pod. | 18/06/2026 | 18/06/2026 | <https://000126.awsstudygroup.com/> |
| 5 | Debug Pod CrashLoopBackOff bằng `kubectl logs` và `kubectl describe`; kiểm tra biến môi trường. | 19/06/2026 | 19/06/2026 | <https://000126.awsstudygroup.com/><br><https://000062.awsstudygroup.com/> |
| 6 | Ôn self-healing của Deployment và reconciliation loop; tổng kết so sánh ECS vs EKS. | 20/06/2026 | 20/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 9:

* Tạo EKS cluster và kết nối bằng kubectl thành công.
* Hiểu vòng đời Pod, Deployment self-healing và các loại Service.
* Debug được CrashLoopBackOff (thiếu biến môi trường).

### Khó khăn và cách giải quyết:

* Pods CrashLoopBackOff do image/env lỗi → dùng `kubectl logs` / `describe` để phát hiện thiếu biến môi trường bắt buộc.

### Kế hoạch tuần tiếp theo:

* Tìm hiểu Data & Analytics: Athena, Glue và QuickSight.
