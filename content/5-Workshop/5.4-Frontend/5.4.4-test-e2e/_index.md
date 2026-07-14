---
title: "End-to-end test"
date: 2026-07-14
weight: 4
chapter: false
pre: " 5.4.4. "
---

I opened the website endpoint in a browser, pasted a long URL, created a short link, and confirmed redirect to the original URL. I also checked CORS in DevTools Network: the `POST` to the Function URL returned `Access-Control-Allow-Origin: *`.

Website: `http://url-shortener-frontend-forward.s3-website-ap-southeast-1.amazonaws.com`

![e2e test](/images/5-Workshop/5.4-Frontend/test-result.png)

![cors network](/images/5-Workshop/5.4-Frontend/cors-network.png)
