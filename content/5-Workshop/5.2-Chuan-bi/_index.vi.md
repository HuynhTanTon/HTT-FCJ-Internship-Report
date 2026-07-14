---
title: "Chuẩn bị"
date: 2026-07-14
weight: 2
chapter: false
pre: " 5.2. "
---

#### Tài nguyên cố định đã dùng

| Thành phần | Giá trị |
|---|---|
| DynamoDB table | `url-shortener-links` (partition key `shortCode` — String) |
| Region | `ap-southeast-1` (Singapore) |
| Lambda function | `url-shortener-backend` |
| IAM Role | `url-shortener-lambda-role` |
| S3 bucket | `url-shortener-frontend-forward` |

Mình tạo bảng DynamoDB `url-shortener-links` ở Singapore, partition key `shortCode` (String), capacity mode **On-demand**, trạng thái Active.

![create-table](/images/5-Workshop/5.2-Chuan-bi/create-table.png)

#### IAM Role đã gắn cho Lambda

Role `url-shortener-lambda-role` có **2 policy**:

1. `AWSLambdaBasicExecutionRole` (AWS managed) — ghi log CloudWatch.
2. `url-shortener-dynamodb-policy` (Customer inline) — đọc/ghi bảng `url-shortener-links`.

![iam-role](/images/5-Workshop/5.2-Chuan-bi/iam-role.png)

Nội dung policy `url-shortener-dynamodb-policy` mình đã gắn:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowDynamoDBAccessToShortenerTable",
      "Effect": "Allow",
      "Action": ["dynamodb:PutItem", "dynamodb:GetItem", "dynamodb:UpdateItem"],
      "Resource": "arn:aws:dynamodb:ap-southeast-1:<ACCOUNT_ID>:table/url-shortener-links"
    }
  ]
}
```
