Need to transfer files? 📂 FTP is specially designed for efficient file transfers and can be faster than HTTP! 🚀

---

### **🔑 FTP Basics**

*   **Purpose**: Transfer files between client and server 📤📥
*   **Default Port**: TCP 21 🎯
*   **Data Transfer**: Uses separate connection 🔄

---

### **⌨️ Essential FTP Commands**

**Authentication** 🔐
*   `USER` - Enter username 👤
*   `PASS` - Enter password 🔒

**File Operations** 📂
*   `RETR` - Download file from server 📥
*   `STOR` - Upload file to server 📤
*   `LIST` - List directory contents 📋
*   `CWD` - Change working directory 📁
*   `PWD` - Print working directory 🗺️
*   `MKD` - Make new directory 📂
*   `RMD` - Remove directory 🗑️
*   `DELE` - Delete file 🗑️
*   `TYPE` - Set transfer type (ASCII/Binary) 🔧

**Connection Management** 🔌
*   `QUIT` - Close FTP session 👋
*   `PASV` - Enter passive mode 🎭
*   `PORT` - Enter active mode 🎯

---

### **🛠️ Practical FTP Session**

**Connecting to Server** 💻:
```bash
ftp 10.10.190.138
```

**Step-by-Step Login** 👣:
1. **Username**
2. **Password**
3. **Exit**: `quit` 👋

---

### **📋 Example Session Output**

```
ftp> ls
-rw-r--r-- 1 0 0 1480 coffee.txt
-rw-r--r-- 1 0 0 14 flag.txt  
-rw-r--r-- 1 0 0 1595 tea.txt

ftp> get coffee.txt
226 Transfer complete.
1480 bytes received
```

---

### **🔍 Behind the Scenes**

*   **Client commands** show in **red** 🔴
*   **Server responses** show in **blue** 🔵
*   **`ls` command** becomes `LIST` on the server 🔄
*   **Directory listings** and **file transfers** use separate connections 🌐

---

### **💡 Pro Tip**
Use `binary` mode for most file transfers (images, executables) and `ascii` mode only for text files! 📄🖼️

---

### **🎯 Quick Summary**

FTP is your go-to for fast file transfers! Perfect for uploading/downloading files between computers. 💪✨