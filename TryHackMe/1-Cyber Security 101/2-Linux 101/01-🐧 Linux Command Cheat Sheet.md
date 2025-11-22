## **👥 User Management & Permissions**

### **🔄 Switching Users**
- `su newuser` : change user to "newuser" (requires the new user's password) 🔄👤
- `cat /etc/passwd` : lists all users on the system 📜👥
- `sudo (command)` : execute a command with superuser privileges 🦸‍♂️⚡
- `passwd` : change your own password 🔑

---

## **📁 File Operations**

### **📄 Viewing & Creating Files**
- `cat (document path)` : reads the document 👀
- `touch (document name)` : creates a new document 🆕
- `mkdir (folder name)` : creates a new folder 🆕📁
- `file (document)` : gives the type of document 📊

### **📋 Listing & Navigation**
- `ls (path)` : lists all files in the path 📂
- `ls -la` : shows all files including hidden ones with details 👀🔍
- `pwd` : shows your current location 🗺️
- `cd (path)` : change directory to the path 🚶‍♂️
- `cd ..` : go up one directory level ⬆️
- `cd ~` or `cd` : go to your home directory 🏠

---

## **🔐 Permissions & Ownership**

### **👮‍♂️ Changing Permissions**
- `chmod (permissions) (file)` : change file permissions (e.g., `chmod 755 script.sh`) 🔧
- `chown (user):(group) (file)` : change file owner and group 👑
- `ls -l` : view detailed file permissions and ownership 📋👀

---

## **✂️ File Management**

### **📤 Moving & Copying Files**
- `cp (file) (target path)` : copying file to target path 📑➡️📑
- `cp -r (folder) (target path)` : copy a folder recursively 📁➡️📁
- `mv (file) (new path)` : moves file to new location 🛣️
- `mv (file) (new name)` : renames file or changes extension ✂️

### **🗑️ Removing Files & Folders**
- `rm (document name)` : deletes the document ❌
- `rm -f (document name)` : deletes the document certainly 💥
- `rm -r (folder name)` : deletes the folder recursively 📁❌
- `rm -rf (folder name)` : deletes the folder certainly 💥📁

---

## **🔍 Searching & Finding**

### **📌 Location & Content Search**
- `find (path) -name (filename)` : find files by name 🔎
- `grep (pattern) (file)` : search for text patterns inside files 🕵️‍♂️
- `which (command)` : shows the full path of a command 🗺️
- `locate (filename)` : quickly find files using database 🚀

---

## **💻 System Information**

### **🔍 System & User Info**
- `whoami` : shows which user you are 👤❓
- `uname -a` : gives OS information 💾ℹ️
- `df -h` : shows disk space usage in human-readable format 💽
- `free -h` : shows memory usage in human-readable format 🧠
- `top` or `htop` : shows running processes and system resources 📊

---

## **📝 Text & Output Management**

### **📢 Echo Commands**
- `echo (something)` : outputs any text we provide 🔊
- `echo > (file) (text)` : writes text to a file (overwrites) 📄✍️
- `echo >> (file) (text)` : appends text to a file 📥➕

### **✂️ Text Processing**
- `head (file)` : show first 10 lines of a file 📄
- `tail (file)` : show last 10 lines of a file 📄
- `tail -f (file)` : follow a file as it grows (great for logs) 👀📈

---

## **🌐 Network Commands**

### **📡 Connectivity & Info**
- `ping (host)` : test connectivity to a host 🏓
- `curl (url)` : transfer data from or to a server 🌐
- `wget (url)` : download files from the web 📥

---

### **💡 Pro Tips** 
- Combine commands with `&&` for powerful workflows 🔗⚡
- `history` shows all previous commands in current sessions 💕
- Use `-f` flag carefully - it forces deletion without asking! ⚠️🎯
- `mv` can both move AND rename files - double duty! 🎪
- Use `Ctrl + C` to stop any running command 🛑
- Use `Ctrl + Z` to pause a process and `bg` to run it in background ⏸️
- Use `man (command)` to read the manual for any command 📚
- Tab completion is your best friend! Press `Tab` to auto-complete filenames 🎯

