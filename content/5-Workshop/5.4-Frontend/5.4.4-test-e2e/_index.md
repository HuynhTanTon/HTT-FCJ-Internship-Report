---
title: "End-to-end test"
date: 2026-07-14
weight: 4
chapter: false
pre: " 5.4.4. "
---

#### Browser scenario I ran

1. Open the website endpoint:  
   `http://url-shortener-frontend-forward.s3-website-ap-southeast-1.amazonaws.com`
2. Paste a long URL (report GitHub Pages / `https://www.google.com`).
3. Click **Create short link** → UI shows a `shortUrl` as Function URL + `shortCode`.
4. Open `shortUrl` → browser redirects to the original URL.
5. (Optional) call `/stats/{shortCode}` or inspect `clickCount` in DynamoDB.

![e2e test](/images/5-Workshop/5.4-Frontend/test-result.png)

#### CORS check in DevTools

Because the S3 website origin **differs** from the Lambda Function URL origin, the browser requires preflight:

- `OPTIONS` (preflight) → 200
- `POST`/`fetch` create → 200 + JSON body

In the **Network** tab (**Preserve log**), Function URL traffic showed successful preflight and fetch — CORS on Function URL and Lambda response headers matched.

![cors network](/images/5-Workshop/5.4-Frontend/cors-network.png)

#### Why this test matters

This is the first full **S3 → Lambda → DynamoDB → redirect** path on a real browser, not only curl against the backend. Skipping the UI would miss CORS failures — a common issue when pairing a static frontend with Function URL.
