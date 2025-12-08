### **🌐 Web Browsing with HTTP & HTTPS**

When you open your browser, you're mainly using two protocols:
*   **HTTP** 🌐: **H**yper**t**ext **T**ransfer **P**rotocol
*   **HTTPS** 🔒: **HTTP** **S**ecure (The 'S' means your connection is encrypted!)

**Key Idea:** These protocols define how your **web browser** 🖥️ "talks" to a **web server** 🖥️.

---

### **📡 Common HTTP Methods (Browser Commands)**

Your browser sends these commands to the server:

*   **`GET`** 📥
    *   **Use:** Retrieves data from the server.
    *   **Example:** Getting an HTML file or an image.

*   **`POST`** 📮
    *   **Use:** Submits *new* data to the server.
    *   **Example:** Submitting a login form or uploading a file.

*   **`PUT`** 💾
    *   **Use:** Creates a new resource or *overwrites* an existing one.

*   **`DELETE`** 🗑️
    *   **Use:** Deletes a specified file or resource.

---

### **🔌 Port Numbers**

*   **HTTP** uses **Port 80** 🌐
*   **HTTPS** uses **Port 443** 🔒
*   **Less common ports:** 8080 & 8443.

---

### **🔍 Peeking Behind the Curtain**

Even though your browser displays a perfect webpage 🖼️, a lot of "conversation" happens in the background that you don't see.

**Using Wireshark** 🦈:
*   A tool like Wireshark lets us spy on this conversation.
*   **Browser text** is shown in **red** 🔴.
*   **Server responses** are shown in **blue** 🔵.
*   You can see hidden details like the **web server version** and when a page was **last modified**.

---

### **👨‍💻 Talking HTTP Directly with `telnet`**

You can manually "talk" to a web server using the `telnet` client! 💬

**Example:**
To get the default page from a server at `10.10.190.138` on port `80`, you would type:

```http
GET / HTTP/1.1
Host: anything
```

**💡 Pro Tip:** You can access any page, not just the default!
*   To get `file.html`, just send: `GET /file.html HTTP/1.1`
*   This is a super efficient way to **troubleshoot** issues directly with the server! 🛠️

---

### **🎯 Key Takeaway**

Understanding these basic HTTP commands and how the browser-server conversation works is a fundamental skill for web development and troubleshooting! 💪