---
title: "CloudWatch Lambda errors"
date: 2026-07-14
weight: 5
chapter: false
pre: " <b> 3.5. </b> "
---

# How to get notified on specific Lambda function error patterns using CloudWatch

#### 1. Thông tin nguồn

| Hạng mục | Nội dung |
| --- | --- |
| Tiêu đề gốc | How to get notified on specific Lambda function error patterns using CloudWatch |
| Nguồn | [AWS Cloud Operations Blog](https://aws.amazon.com/blogs/mt/get-notified-specific-lambda-function-error-patterns-using-cloudwatch/) |
| Chủ đề | CloudWatch Logs filter, Lambda Errors metric vs log pattern, SNS thông báo |

#### 2. Tóm tắt nội dung

Bài viết chỉ ra hạn chế của CloudWatch Alarm trên metric **Errors** của Lambda: biết *có lỗi* nhưng **không kèm chi tiết** log. Giải pháp đề xuất: dùng **CloudWatch Logs subscription / filter pattern** (ví dụ `ERROR`, `CRITICAL`, pattern tùy chỉnh) để bắt dòng log quan trọng, kích hoạt một Lambda “error processing”, rồi publish sang **SNS** (email/SMS…) kèm nội dung lỗi cụ thể — tiện hành động nhanh hơn là chỉ nhìn alarm đỏ.

#### 3. Nội dung chính

**3.1. Metric Errors vs filter trên log**

- Alarm trên metric Errors = tín hiệu tổng hợp.
- Filter trên log = bắt đúng chuỗi/`[ERROR]` trong CloudWatch Logs của function.

**3.2. Luồng tham chiếu trong bài**

Log group Lambda → filter pattern khớp → (Lambda xử lý lỗi) → SNS → email người vận hành.

**3.3. Filter pattern**

Có thể dùng pattern đơn giản hoặc tổ hợp (`?ERROR ?WARN ?5xx`…). Tài liệu filter syntax của CloudWatch Logs là phần bổ sung cần đọc khi tinh chỉnh.

#### 4. Nhận xét (liên hệ dự án)

Ở mục **5.5**, mình làm biến thể cùng ý tưởng “log error → cảnh báo”:

1. Metric filter trên `/aws/lambda/url-shortener-backend` với pattern `"[ERROR]"`.
2. Metric `URLShortenerErrorCount` + Alarm `url-shortener-error-alarm`.
3. SNS subscribe email.

Khác một chút so với bài (bài dùng subscription → Lambda trung gian để đưa **nội dung log** vào SNS; mình dùng metric filter → alarm → SNS cho tín hiệu số lượng lỗi). Cùng mục tiêu vận hành: biết sớm khi handler ghi lỗi. Trạng thái **Insufficient data** trên alarm khi chưa có `[ERROR]` là bình thường — cũng là điểm cần hiểu khi đọc CloudWatch, không phải alarm “hỏng”.
