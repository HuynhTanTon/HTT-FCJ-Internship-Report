---
title: "Test end-to-end"
date: 2026-07-14
weight: 4
chapter: false
pre: " 5.4.4. "
---

Mình mở website endpoint trên trình duyệt, dán link dài, tạo link ngắn và xác nhận redirect về URL gốc thành công. Đồng thời kiểm tra CORS trên tab Network (DevTools): request `POST` tới Function URL trả về kèm `Access-Control-Allow-Origin: *`.

Website: `http://url-shortener-frontend-forward.s3-website-ap-southeast-1.amazonaws.com`

![e2e test](/images/5-Workshop/5.4-Frontend/test-result.png)

![cors network](/images/5-Workshop/5.4-Frontend/cors-network.png)
