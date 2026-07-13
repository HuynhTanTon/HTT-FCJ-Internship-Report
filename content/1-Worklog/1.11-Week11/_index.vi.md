---
title: "Worklog Tuần 11"
date: 2024-01-01
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

**Thời gian:** 29/06/2026 – 05/07/2026

### Mục tiêu tuần 11:

* Thực hành AI/ML trên AWS: SageMaker, Rekognition, Comprehend, Bedrock.
* Phân biệt AI Services dùng ngay và ML Platform để tự train model.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | Tìm hiểu AI Services (Rekognition, Comprehend) vs ML Platform (SageMaker); tổng quan Generative AI / Bedrock. | 29/06/2026 | 29/06/2026 | <https://000056.awsstudygroup.com/><br><https://cloudjourney.awsstudygroup.com/> |
| 3 | Lab 1: Khởi tạo SageMaker Notebook Instance; train model Image Classification. | 30/06/2026 | 01/07/2026 | <https://000056.awsstudygroup.com/><br><https://cloudjourney.awsstudygroup.com/> |
| 4 | Deploy SageMaker Endpoint; gọi API inference (độ chính xác ~91% trên tập test). | 02/07/2026 | 02/07/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | Thực hành tích hợp AI qua API; tìm hiểu Foundation Models trên Amazon Bedrock. | 03/07/2026 | 03/07/2026 | <https://000056.awsstudygroup.com/><br><https://cloudjourney.awsstudygroup.com/> |
| 6 | Viết Lambda tự động xóa SageMaker Endpoint sau khi test để tránh chi phí; tổng kết tuần. | 04/07/2026 | 04/07/2026 | <https://000022.awsstudygroup.com/><br><https://000066.awsstudygroup.com/> |

### Kết quả đạt được tuần 11:

* Phân biệt AI Services và ML Platform (SageMaker).
* Train và deploy model phân loại ảnh trên SageMaker (~91% accuracy).
* Hiểu cách dùng Bedrock Foundation Models qua API thống nhất.

### Khó khăn và cách giải quyết:

* Endpoint deploy ~7 phút và dễ quên xóa → viết Lambda tự động xóa endpoint sau khi test.

### Kế hoạch tuần tiếp theo:

* Tổng kết chương trình, hoàn thiện project cuối khóa và chuẩn bị báo cáo thực tập.
