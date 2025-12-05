Using multiple devices? 📱💻 IMAP keeps your email synchronized across all of them! Unlike POP3, IMAP maintains messages on the server for seamless multi-device access. 🔄

---

### **🆚 IMAP vs POP3**

**POP3** 📥:
*   Downloads & deletes from server 🗑️
*   Best for **single device** use 🖥️
*   Minimal server storage usage 💾

**IMAP** 🔄:
*   Keeps messages on server ☁️
*   Syncs across **multiple devices** 📱💻
*   More server storage needed 💽
*   Syncs read status, moves, deletions 📊

---

### **🔑 Essential IMAP Commands**

**Authentication** 🔐
*   `LOGIN <username> <password>` - Authenticate user 👤

**Mailbox Operations** 📁
*   `SELECT <mailbox>` - Choose folder (e.g., "inbox") 📂
*   `FETCH <number> <data>` - Retrieve message content 📥
*   `MOVE <numbers> <mailbox>` - Move messages to folder 🔄
*   `COPY <numbers> <mailbox>` - Copy messages to folder 📋
*   `LOGOUT` - End session 👋

---

### **🛠️ IMAP Session via Telnet**

**Default Port**: TCP 143 🎯

**Connect to Server** 💻:
```bash
telnet 10.10.190.138 143
```

---

### **📋 Complete IMAP Session Example**

```
* OK Dovecot (Ubuntu) ready.
A LOGIN strategos 
A OK Logged in
B SELECT inbox
* 4 EXISTS
* 0 RECENT
B OK Select completed
C FETCH 3 body[]
* 3 FETCH (BODY[] {445}
Return-path: <user@client.thm>
To: strategos@server.thm  
Subject: Telnet email

Hello. I am using telnet to send you an email!
)
C OK Fetch completed
D LOGOUT
* BYE Logging out
```

---

### **🔍 Behind the Scenes**

*   **Client commands** in **red** 🔴 (A, B, C, D)
*   **Server responses** in **blue** 🔵
*   **Complex protocol** with more features than POP3 🎛️
*   **Server maintains** message state and folders 🗂️

---

### **💡 Key IMAP Features**

*   **Folder synchronization** across devices 📂
*   **Message status** tracking (read/unread) 👁️
*   **Server-side** search and organization 🔍
*   **Multiple mailbox** support 🗄️

---

### **🎯 Quick Summary**

**Choose IMAP when:**
- Using multiple devices 📱💻🖥️
- Want to keep emails on server ☁️
- Need folder synchronization 🔄

**Choose POP3 when:**
- Single device usage 🖥️
- Want to download and delete 🗑️
- Limited server storage 💾

Now you're an email protocol expert! 📧🎓✨