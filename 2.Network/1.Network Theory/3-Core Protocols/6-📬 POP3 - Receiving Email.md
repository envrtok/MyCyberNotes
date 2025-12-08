Now that you can **send** email with SMTP, let's learn how to **receive** it! 📥 POP3 (Post Office Protocol version 3) lets your mail client retrieve messages from the server.

---

### **🏣 The Mailbox Analogy**

*   **SMTP** 📤 = Dropping off mail at the post office
*   **POP3** 📥 = Checking your mailbox for new letters

---

### **🔑 Essential POP3 Commands**

**Authentication** 🔐
*   `USER <username>` - Identify yourself 👤
*   `PASS <password>` - Provide password 🔒

**Message Management** 📋
*   `STAT` - Check message count and total size 📊
*   `LIST` - List all messages with sizes 📜
*   `RETR <number>` - Retrieve specific message 📥
*   `DELE <number>` - Mark message for deletion 🗑️
*   `QUIT` - End session and apply changes 👋

---

### **🛠️ POP3 Session via Telnet**

**Default Port**: TCP 110 🎯

**Connect to Server** 💻:
```bash
telnet 10.10.190.138 110
```

**Sample Credentials** 🔑:
*   **Username**: `linda` 👩‍💼
*   **Password**: `Pa$$123` 🔒

---

### **📋 Complete POP3 Session Example**

```
+OK Dovecot (Ubuntu) ready.
USER strategos
+OK
PASS 
+OK Logged in.
STAT
+OK 3 1264
LIST
+OK 3 messages:
1 407
2 412 
3 445
.
RETR 3
+OK 445 octets
Return-path: <user@client.thm>
To: strategos@server.thm
Subject: Telnet email

Hello. I am using telnet to send you an email!
.
QUIT
+OK Logging out.
```

---

### **🔍 Behind the Scenes**
*   **Client commands** in **red** 🔴
*   **Server responses** in **blue** 🔵
*   **Passwords are visible** in plain text! 👀
*   **Network sniffers** can read all traffic 📡

---

### **⚠️ Security Note**

POP3 sends passwords **unencrypted**! 🚨
*   Anyone capturing network traffic can see your login credentials
*   Consider using secure alternatives when possible 🔒

---

### **🔄 Email Flow Summary**

1. **Send** email → **SMTP** 📤
2. **Receive** email → **POP3** 📥
3. **Complete** email communication cycle! 🔄

---

### **🎯 Quick Summary**

POP3 completes the email picture - now you can both send AND receive emails using standard protocols! 📧✨