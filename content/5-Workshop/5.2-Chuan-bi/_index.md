---
title: "Prerequisites"
date: 2026-07-14
weight: 2
chapter: false
pre: " 5.2. "
---

#### Fixed resources used

| Component | Value |
|---|---|
| DynamoDB table | `url-shortener-links` (partition key `shortCode` — String) |
| Region | `ap-southeast-1` (Singapore) |
| Lambda function | `url-shortener-backend` |
| IAM Role | `url-shortener-lambda-role` |
| S3 bucket | `url-shortener-frontend-forward` |

I created DynamoDB table `url-shortener-links` in Singapore with partition key `shortCode` (String), **On-demand** capacity, status Active.

![create-table](/images/5-Workshop/5.2-Chuan-bi/create-table.png)

#### IAM role attached to Lambda

Role `url-shortener-lambda-role` has **2 policies**:

1. `AWSLambdaBasicExecutionRole` (AWS managed) — CloudWatch logging.
2. `url-shortener-dynamodb-policy` (Customer inline) — read/write table `url-shortener-links`.

![iam-role](/images/5-Workshop/5.2-Chuan-bi/iam-role.png)

Contents of `url-shortener-dynamodb-policy`:

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
