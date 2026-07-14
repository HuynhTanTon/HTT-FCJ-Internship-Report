---
title: "Test API"
date: 2026-07-14
weight: 2
chapter: false
pre: " 5.3.2. "
---

#### Short-link creation test

I called the create API with `curl` (and later via the UI once the frontend was ready):

```bash
curl -X POST https://<function-url>/ \
  -H "Content-Type: application/json" \
  -d '{"url":"https://www.google.com"}'
```

Sample response:

```json
{ "shortCode": "aZ3kT9", "shortUrl": "https://<function-url>/aZ3kT9", "originalUrl": "https://www.google.com" }
```

![Short link result in the UI](/images/5-Workshop/5.3-Backend/frontend-shorten-result.png)

#### Redirect test

Opening a short URL in the browser returns **302** to the original URL. I verified the status with PowerShell:

```powershell
Invoke-WebRequest -Uri "https://<function-url>/<shortCode>" -MaximumRedirection 0
```

![Test redirect HTTP 302](/images/5-Workshop/5.3-Backend/test-redirect-302.png)

#### Stats test

```bash
curl https://<function-url>/stats/<shortCode>
```

```json
{ "shortCode": "aZ3kT9", "originalUrl": "https://www.google.com", "clickCount": 1, "createdAt": "..." }
```

#### DynamoDB verification

In DynamoDB → table `url-shortener-links` → **Explore table items**, I confirmed items were created/updated correctly (`shortCode`, `originalUrl`, `clickCount`, `createdAt`).

![dynamodb items](/images/5-Workshop/5.3-Backend/dynamodb-items.png)
