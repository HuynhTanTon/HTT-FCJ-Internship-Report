---
title: "Worklog Tuần 10"
date: 2024-01-01
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

**Thời gian:** 22/06/2026 – 28/06/2026

### Mục tiêu tuần 10:

* Xây dựng data lake trên AWS: S3 + Glue + Athena + QuickSight.
* Truy vấn dữ liệu lớn trên S3 mà không cần database server truyền thống.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | Tìm hiểu kiến trúc data lake: S3 (storage), Glue (ETL), Athena (query), QuickSight (BI). | 22/06/2026 | 22/06/2026 | <https://000070.awsstudygroup.com/><br><https://000035.awsstudygroup.com/> |
| 3 | Lab 1: Upload dataset CSV (~100.000 dòng) lên S3; tạo bảng Athena và chạy SQL trực tiếp trên S3. | 23/06/2026 | 24/06/2026 | <https://000106.awsstudygroup.com/><br><https://000040.awsstudygroup.com/> |
| 4 | Thực hành AWS Glue Crawler / ETL; xử lý lỗi DynamicFrame (convert `toDF()` sang Spark DataFrame). | 25/06/2026 | 25/06/2026 | <https://000040.awsstudygroup.com/><br><https://000105.awsstudygroup.com/> |
| 5 | Tối ưu chi phí Athena: định dạng Parquet, partition theo ngày; trực quan hóa với QuickSight. | 26/06/2026 | 26/06/2026 | <https://000073.awsstudygroup.com/><br><https://000106.awsstudygroup.com/> |
| 6 | Tổng hợp pipeline S3 → Glue → Athena → QuickSight; ghi chú best practices chi phí. | 27/06/2026 | 27/06/2026 | <https://000070.awsstudygroup.com/><br><https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 10:

* Chạy SQL trên dữ liệu lớn trong S3 bằng Athena không cần DB server.
* Hiểu ETL với Glue và tối ưu Athena bằng Parquet + partition.
* Biết dùng QuickSight để visualization.

### Khó khăn và cách giải quyết:

* Glue Job fail do dùng sai API DynamicFrame → theo Glue Developer Guide, convert bằng `toDF()` sang Spark DataFrame.

### Kế hoạch tuần tiếp theo:

* Khám phá AI/ML Services: SageMaker, Rekognition và Amazon Bedrock.
