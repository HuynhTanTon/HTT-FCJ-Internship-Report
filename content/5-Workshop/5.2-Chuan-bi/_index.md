---
title: "Prerequisites"
date: 2026-07-14
weight: 2
chapter: false
pre: " 5.2. "
---

#### Goal

Prepare the foundation (data table + IAM permissions) so Lambda only needs to attach a role and run code, without mid-flight policy fixes.

#### Fixed resources used

| Component | Actual value |
|---|---|
| Region | `ap-southeast-1` (Singapore) |
| DynamoDB table | `url-shortener-links` |
| Partition key | `shortCode` (String) |
| Capacity mode | On-demand |
| Lambda function | `url-shortener-backend` |
| IAM Role | `url-shortener-lambda-role` (or the execution role attached at create time) |
| S3 bucket | `url-shortener-frontend-forward` |

#### DynamoDB table

I created `url-shortener-links` with:

- **Partition key:** `shortCode` (S) — enough for lookup by short code.
- **No sort key** — each `shortCode` is one independent item.
- **On-demand** — fits lab traffic without sizing RCU/WCU upfront.

Attributes like `originalUrl`, `clickCount`, and `createdAt` are written on Put/Update; DynamoDB does not require a relational-style schema declaration first.

![create-table](/images/5-Workshop/5.2-Chuan-bi/create-table.png)

#### IAM role for Lambda

The Lambda execution role has at least two permission layers:

1. `AWSLambdaBasicExecutionRole` (AWS managed) — write CloudWatch Logs.
2. A DynamoDB policy (customer inline / managed) — only required actions on the table ARN.

![iam-role](/images/5-Workshop/5.2-Chuan-bi/iam-role.png)

DynamoDB policy content (replace `<ACCOUNT_ID>`):

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowDynamoDBAccessToShortenerTable",
      "Effect": "Allow",
      "Action": [
        "dynamodb:PutItem",
        "dynamodb:GetItem",
        "dynamodb:UpdateItem"
      ],
      "Resource": "arn:aws:dynamodb:ap-southeast-1:<ACCOUNT_ID>:table/url-shortener-links"
    }
  ]
}
```

**Least privilege:** no `Scan`/`DeleteItem`/`*` across the region — enough for create + redirect Update + stats read. Missing `UpdateItem` breaks click increments on redirect.

#### Notes before Backend

- DynamoDB region, Lambda region, and `TABLE_NAME` must match (`url-shortener-links`).
- S3 bucket names are globally unique; I used suffix `forward` → `url-shortener-frontend-forward`.
