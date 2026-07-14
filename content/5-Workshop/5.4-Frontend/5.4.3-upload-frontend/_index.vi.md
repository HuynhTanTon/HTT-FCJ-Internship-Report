---
title: "Upload frontend & cấu hình Function URL"
date: 2026-07-14
weight: 3
chapter: false
pre: " 5.4.3. "
---

#### Object đã upload

Trên tab **Objects** của bucket `url-shortener-frontend-forward`, mình upload:

| File | Vai trò |
| ---- | ------- |
| `index.html` | UI nhập URL dài, gọi API, hiển thị `shortUrl` |
| `config.js` | Khai báo `API_BASE_URL` / Function URL thật của Lambda |
| `forest-anime-bg.png` | Ảnh nền giao diện |

![upload-files](/images/5-Workshop/5.4-Frontend/upload-files.png)

#### Vai trò `config.js`

Thay vì hard-code Function URL trong HTML, mình tách cấu hình sang `config.js` để:

- Đổi endpoint Lambda mà không sửa logic UI nhiều.
- Dễ đối chiếu khi screenshot / báo cáo (file config rõ ràng trên S3).

Nội dung `config.js` thực chất trỏ về Function URL đã copy ở mục 5.3.1, ví dụ dạng:

```javascript
window.APP_CONFIG = {
  apiBaseUrl: "https://xxxx.lambda-url.ap-southeast-1.on.aws"
};
```

(`index.html` dùng giá trị này khi `fetch` `POST /`.)

#### Content-Type

Upload qua console thường nhận diện đúng `text/html`, `application/javascript`, `image/png`. Nếu tự upload bằng CLI mà sai Content-Type, trình duyệt có thể không chạy JS đúng — lúc lab mình dùng Upload trên console nên không gặp lỗi này.
