- Lists documents.  
- Usage: **ls (option) (file)**

---

## 🔎 -a or --all
- Lists all documents, includes hidden documents. 👻

---

## 📋 -l
- Lists document with details  
- example result is:
```
total 80  
-rw-rw-r-- 1 tryhackme tryhackme 65522 May 10 2021 access.log  
drwxr-xr-x 2 tryhackme tryhackme 4096 May 10 2021 folder1  
drwxr-xr-x 2 tryhackme tryhackme 4096 May 10 2021 folder2  
drwxr-xr-x 2 tryhackme tryhackme 4096 May 10 2021 folder3  
drwxr-xr-x 2 tryhackme tryhackme 4096 May 10 2021 folder4
```

#### 🧩 First Column
- Gives informations about **permissions** 🔐  
- It has 1+3+3+3 system  
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