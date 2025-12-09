- 🌐 HTTP is the protocol which provides communication between web server and user client.
    - 📤 **HTTP Request**: User sends to server.
    - 📥 **HTTP Response**: Server sends to user.

---
![[Pasted image 20251209173745.png]]

---
### HTTP Message Structure

**Start Line**: Tells what kind of message is sent.

- 📝 Request:
    - `GET /index.html HTTP/1.1`
    - `POST /login HTTP/1.1`
- 📝 Response:
    - `HTTP/1.1 200 OK`
    - `HTTP/1.1 404 Not Found`

---

**Headers**: Gives key-values about the message.

- 📌 Request Headers:
    - `Host: tryhackme.com`
    - `User-Agent: Mozilla/5.0`
    - `Accept: text/html`
- 📌 Response Headers:
    - `Content-Type: application/json`
    - `Set-Cookie: sessionid=abc123`
    - `Cache-Control: no-cache`

---

**Body**: Actual data.

- 📤 Request Bodies:
    - `username=aleksandra&password=securepassword`
    - `{"search":"http messages"}`
- 📥 Response Bodies:
    - `{"message": "Login successful!", "status": "success"}`
    - `<html><body><h1>Welcome!</h1></body></html>`
---