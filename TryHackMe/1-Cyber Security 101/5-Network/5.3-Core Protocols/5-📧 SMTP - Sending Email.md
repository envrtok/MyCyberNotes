Just like web browsing and file transfers, sending email has its own protocol! 📮 SMTP defines how mail clients and servers communicate with each other.

---

### **🏣 The Post Office Analogy**

Think of SMTP like visiting a post office: 🏤
*   **Greet** the employee 👋
*   **Specify** destination 📍
*   **Provide** sender info 📄
*   **Hand over** the package 📦

---

### **🔑 Essential SMTP Commands**

**Session Initiation** 🚀
*   `HELO` or `EHLO` - Start SMTP session 📞

**Address Specification** 📧
*   `MAIL FROM` - Set sender's email address 👤
*   `RCPT TO` - Set recipient's email address 🎯

**Message Transfer** 📝
*   `DATA` - Begin sending email content 📤
*   `.` (single period) - End the email message ⏹️

**Connection Management** 🔌
*   `QUIT` - Close SMTP session 👋

---

### **🛠️ Sending Email via Telnet**

**Default Port**: TCP 25 🎯

**Example Session** 💻:
```bash
telnet 10.10.190.138 25
```

**Step-by-Step Process** 👣:
1. **Connect** to SMTP server 🔗
2. **Greet** with `HELO client.thm` 👋
3. **Set sender** with `MAIL FROM: <user@client.thm>` 👤
4. **Set recipient** with `RCPT TO: <strategos@server.thm>` 🎯
5. **Start data** with `DATA` 📝
6. **Write email** (headers + body) ✍️
7. **End with** `.` on its own line ⏹️
8. **Close** with `QUIT` 👋

---

### **📋 Complete Example Output**

```
220 example.thm ESMTP Exim 4.95 Ubuntu
HELO client.thm
250 example.thm Hello client.thm
MAIL FROM: <user@client.thm>
250 OK
RCPT TO: <strategos@server.thm>
250 Accepted
DATA
354 Enter message, ending with "." on a line by itself
From: user@client.thm
To: strategos@server.thm
Subject: Telnet email

Hello. I am using telnet to send you an email!
.
250 OK id=1sMrpq-0001Ah-UT
QUIT
221 example.thm closing connection
```

---

### **🔍 Behind the Scenes**

*   **Client commands** in **red** 🔴
*   **Server responses** in **blue** 🔵
*   **Manual telnet** helps understand what email clients do automatically 🤖

---

### **🎓 What You've Learned**

Now you understand how **text-based protocols** work! 🎯
*   **HTTP** 🌐 - Web browsing
*   **FTP** 📁 - File transfers  
*   **SMTP** 📧 - Email sending

This makes learning other protocols like **POP3** and **IMAP** much easier! 📚✨

---

### **🎯 Quick Summary**

SMTP is the protocol that powers email delivery - and now you know exactly how it works behind the scenes! 💪🚀