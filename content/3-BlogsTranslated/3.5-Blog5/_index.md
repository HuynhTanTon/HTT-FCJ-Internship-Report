---
title: "CloudWatch Lambda errors"
date: 2026-07-14
weight: 5
chapter: false
pre: " <b> 3.5. </b> "
---

# How to get notified on specific Lambda function error patterns using CloudWatch

#### 1. Source information

| Item | Details |
| --- | --- |
| Original title | How to get notified on specific Lambda function error patterns using CloudWatch |
| Source | [AWS Cloud Operations Blog](https://aws.amazon.com/blogs/mt/get-notified-specific-lambda-function-error-patterns-using-cloudwatch/) |
| Topics | CloudWatch Logs filters, Lambda Errors metric vs log patterns, SNS alerts |

#### 2. Summary

The article notes that CloudWatch Alarms on Lambda’s **Errors** metric tell you *that* something failed but not **what** the log said. The proposed approach uses a **CloudWatch Logs subscription / filter pattern** (e.g. `ERROR`, `CRITICAL`, custom text) to catch important lines, invoke an “error processing” Lambda, then publish to **SNS** with concrete error details — faster to act on than a red alarm alone.

#### 3. Main content

**3.1. Errors metric vs log filters** — Errors alarms are aggregate signals; log filters catch specific strings like `[ERROR]` in the function’s log group.

**3.2. Reference flow** — Lambda log group → matching filter → (processor Lambda) → SNS → operator email.

**3.3. Filter patterns** — simple or combined patterns (`?ERROR ?WARN ?5xx`…); CloudWatch Logs filter syntax docs help refine matches.

#### 4. Reflection (project link)

In **section 5.5** I implemented a related “log error → alert” path:

1. Metric filter on `/aws/lambda/url-shortener-backend` with pattern `"[ERROR]"`.
2. Metric `URLShortenerErrorCount` + Alarm `url-shortener-error-alarm`.
3. SNS email subscription.

Slightly different from the article (subscription → processor Lambda for **log text** in SNS; I used metric filter → alarm → SNS for an **error-count** signal). Same ops goal: notice handler failures early. Alarm **Insufficient data** when no `[ERROR]` lines yet is expected — worth understanding when reading CloudWatch, not a broken alarm.
