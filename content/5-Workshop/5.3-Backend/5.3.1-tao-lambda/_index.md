---
title: "Create Lambda function & Function URL"
date: 2026-07-14
weight: 1
chapter: false
pre: " 5.3.1. "
---

I created the Lambda function with this configuration:

1. **Create function** → Author from scratch
   - Function name: `url-shortener-backend`
   - Runtime: **Node.js 20.x**
   - Execution role: `url-shortener-lambda-role`

2. In the **Code** tab, I replaced `index.mjs` with the URL shortener handler (AWS SDK v3 is available in the Lambda runtime — `@aws-sdk/client-dynamodb`, `@aws-sdk/lib-dynamodb` — so no `npm install` on the console).

3. **Configuration → Environment variables**:
   - `TABLE_NAME` = `url-shortener-links`

4. Enabled **Function URL**:
   - Auth type: `NONE` (public shortener API)
   - CORS: `Access-Control-Allow-Origin: *`, methods `GET, POST`

![lambda](/images/5-Workshop/5.3-Backend/create-lambda.png)

The Function URL (`https://xxxx.lambda-url.ap-southeast-1.on.aws/`) was then used to configure the frontend.
