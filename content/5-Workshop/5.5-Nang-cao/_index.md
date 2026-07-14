---
title: "Advanced (bonus)"
date: 2026-07-14
weight: 5
chapter: false
pre: " 5.5. "
---

#### Goal of the advanced section

After create/redirect worked, I added two more operational pieces: **safe concurrent click counting** and **alerts when Lambda logs errors**.

#### Click counting (`clickCount`)

In the redirect handler (`GET /{shortCode}`), instead of separate Get+Put (race-prone), I used `UpdateCommand` to increment `clickCount` **atomically**:

- `SET clickCount = if_not_exists(clickCount, :zero) + :inc`
- `ConditionExpression: attribute_exists(shortCode)` — missing code → ConditionalCheckFailed → **404**.

Concurrent redirects then increment more correctly than manual read-modify-write. IAM already includes `dynamodb:UpdateItem` (section 5.2).

#### CloudWatch + SNS error alerts

Monitoring chain I configured:

1. **Metric filter** on `/aws/lambda/url-shortener-backend`  
   - Pattern: `"[ERROR]"`  
   - Metric: `URLShortenerErrorCount` (namespace `URLShortener`)
2. **Alarm** `url-shortener-error-alarm` on that metric (~5-minute evaluation window).
3. **SNS** email subscription — confirm before real alert mail arrives.

![cloudwatch alarm](/images/5-Workshop/5.5-Nang-cao/alarm.png)

#### What Insufficient data means

The alarm often shows **Insufficient data** when there are no datapoints yet (no `"[ERROR]"` logs in the evaluation window). That does **not** mean the alarm is broken — only that no error signal arrived. When Lambda logs enough `[ERROR]` lines, the metric rises and the alarm can go **In alarm** and notify SNS.

#### Value added

- `clickCount` turns the demo into a shortener with minimal usage metrics.
- Metric filter + Alarm + SNS shows an **observe → alert** loop without a heavy Grafana stack.
