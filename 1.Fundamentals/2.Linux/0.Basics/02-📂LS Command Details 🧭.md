### **📝 LS Command Overview**
- Lists documents. 📑
- Usage: **ls (option) (file)** 💻
---
### **📋 Option: -l**
- Lists document with details 📊
- example result is:
```
total 80
-rw-rw-r-- 1 tryhackme tryhackme 65522 May 10 2021 access.log
drwxr-xr-x 2 tryhackme tryhackme 4096 May 10 2021 folder1
drwxr-xr-x 2 tryhackme tryhackme 4096 May 10 2021 folder2
drwxr-xr-x 2 tryhackme tryhackme 4096 May 10 2021 folder3
drwxr-xr-x 2 tryhackme tryhackme 4096 May 10 2021 folder4
```

#### **🧩 1st Column**
- Gives informations about **permissions** 🔐
- It has 1+3+3+3 system ➕
- First one gives what kind of file is:
  - `-` means it is regular file 📄
  - `d` means it is a directory 📁
  - `l` means it is a shortcut to another file 🔗
- Other groups gives user permissions:
  - First 3 : Owner Permissions 👤
  - Second 3 : Group Permissions 👥
  - Third 3 : Permissions for Everyone 🌐
- And meaning these permissions:
  - `r` : read 📖
  - `w` : write ✍️
  - `x` : execute ▶️

#### **🔗 2nd Column**
- Number of hard links. 🔢 If it is 1, that means we can access with only document's name. But if it is 2, we can access with folder's name and with "." when we inside the folder. 

#### **👤 3rd Column:** Owner Name

#### **👥 4th Column:** Group Name

#### **📏 5th Column:** File Size (Byte)

#### **📅 6th Column:** Last Modification Date & Time

#### **📛 7th Column:** File/Directory Name
---
### **🔎Quick Options:**

- **-a or --all**: Lists all documents, includes hidden documents. 👻
    
- **-h**: Gives document size much easier to read (64K instead of 65522) 📏
    
- **-t**: Sorts by modification time. ⏰
    
- **-r**: Reverses the list. 🔄
    
- **--author**: Using with -l, gives author information. ✍️
    
- **-g**: Hides group information.
    
- **-R**: Gives all contents of directorys. 📂
    
- **TİP**: You can combine them like that: -la, -lh, -ltr, -lah ... 🔗

---