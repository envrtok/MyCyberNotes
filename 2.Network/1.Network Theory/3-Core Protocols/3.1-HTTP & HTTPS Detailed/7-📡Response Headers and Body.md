## 🏷️ Response Headers

When a web server responds to an HTTP request, it includes **response headers** (key-value pairs).  
These headers provide important info about the response and guide the client (browser) on how to handle it.

👉 Example: Headers like **Content-Type**, **Content-Length**, and **Date** give crucial details about the server’s response.

---

### 📌 Required Response Headers

|🏷️ Header|📌 Example|📖 Description|
|---|---|---|
|📅 **Date**|`Date: Fri, 23 Aug 2024 10:43:21 GMT`|Shows the exact date and time when the response was generated.|
|📄 **Content-Type**|`Content-Type: text/html; charset=utf-8`|Tells the client what type of content is being sent (HTML, JSON, etc.) and the character set.|
|🖥️ **Server**|`Server: nginx`|Indicates the server software handling the request. Useful for debugging, but often hidden for security.|

---

### 🔧 Other Common Response Headers

- 🍪 **Set-Cookie**
    
    - Example: `Set-Cookie: sessionId=38af1337es7a8`
    - Sends cookies from the server to the client.
    - ⚠️ Use **HttpOnly** (not accessible by JavaScript) and **Secure** (only over HTTPS) flags for safety.
- 📦 **Cache-Control**
    
    - Example: `Cache-Control: max-age=600`
    - Defines how long the client can cache the response.
    - Can also enforce `no-cache` for sensitive data.
- 🔀 **Location**
    
    - Example: `Location: /index.html`
    - Used in **3xx redirection responses** to tell the client where to go next.
    - ⚠️ Must be validated to avoid **open redirect vulnerabilities**.

---

## 📦 Response Body

The **Response Body** contains the actual data sent back to the client:

- 🌐 HTML pages
- 🧩 JSON data
- 🖼️ Images
- 📜 XML documents

⚠️ **Security Note:** Always sanitise and escape user-generated content before including it in the response to prevent **XSS (Cross-Site Scripting)** and other injection attacks.