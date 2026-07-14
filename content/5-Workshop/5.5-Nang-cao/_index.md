---
title: "Advanced (bonus)"
date: 2026-07-14
weight: 5
chapter: false
pre: " 5.5. "
---

#### Click counting (`clickCount`)

In the redirect flow (`GET /{shortCode}`), the code uses `UpdateCommand` to increment `clickCount` **atomically**, with `ConditionExpression: attribute_exists(shortCode)` so missing codes return 404. The IAM policy already includes `dynamodb:UpdateItem` (see section 5.2).

#### Error alerts with CloudWatch

I configured error monitoring for Lambda:

1. A metric filter on log group `/aws/lambda/url-shortener-backend` with pattern `"[ERROR]"`, metric `URLShortenerErrorCount` (namespace `URLShortener`).
2. CloudWatch Alarm `url-shortener-error-alarm` on that metric (threshold per alarm settings — state becomes OK / In alarm when datapoints exist).
3. An SNS topic with email subscription for alarm notifications.

![cloudwatch alarm](/images/5-Workshop/5.5-Nang-cao/alarm.png)
