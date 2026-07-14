---
title: "Upload frontend & configure Function URL"
date: 2026-07-14
weight: 3
chapter: false
pre: " 5.4.3. "
---

#### Objects uploaded

On the **Objects** tab of `url-shortener-frontend-forward`, I uploaded:

| File | Role |
| ---- | ------- |
| `index.html` | UI to paste long URLs, call the API, show `shortUrl` |
| `config.js` | Declares the real Lambda Function URL |
| `forest-anime-bg.png` | UI background image |

![upload-files](/images/5-Workshop/5.4-Frontend/upload-files.png)

#### Role of `config.js`

Instead of hard-coding the Function URL in HTML, I split config into `config.js` so I can change the Lambda endpoint without rewriting UI logic, and keep the config visible for the report on S3.

Example shape:

```javascript
window.APP_CONFIG = {
  apiBaseUrl: "https://xxxx.lambda-url.ap-southeast-1.on.aws"
};
```

(`index.html` uses this value for `fetch` `POST /`.)

#### Content-Type

Console Upload usually sets `text/html`, `application/javascript`, and `image/png` correctly. Wrong Content-Type via CLI can break JS execution — I used console Upload for the lab and did not hit that issue.
