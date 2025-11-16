### 🎯 **What is Active Directory?**
- **Central directory** for all network objects 📚
- **Manages users, computers, groups, printers** and more 🖨️
- **Core of Windows Domain** networks 🌐

---

## 👥 **Key Object Types**

### 👤 **Users**
- **Security principals** that can access resources 🔑
- **Two types**:
  - **👨‍💼 People** - Employees & staff
  - **🤖 Services** - For applications like IIS/MSSQL

### 💻 **Machines**
- **Computer accounts** in the domain 🖥️
- **Auto-created** when computers join domain 🔄
- **Naming**: `ComputerName$` (e.g., `DC01$`) 🏷️

### 👨‍👩‍👧‍👦 **Security Groups**
- **Group users/machines** for permissions 👥
- **Members inherit group privileges** 📜
- **Can contain other groups** 🔄

---

## 🏆 **Important Default Groups**

| Group | Description |
|-------|-------------|
| **Domain Admins** 👑 | Full control over entire domain |
| **Server Operators** 🔧 | Administer Domain Controllers |
| **Backup Operators** 💾 | Access all files for backups |
| **Account Operators** 👤 | Create/modify user accounts |
| **Domain Users** 👥 | All user accounts in domain |
| **Domain Computers** 💻 | All computers in domain |

---

## 📊 **Organizational Units (OUs)**
- **Container objects** for organizing users/computers 📁
- **Apply policies** to entire departments 🎯
- **User can only be in ONE OU** at a time 1️⃣

### 🏢 **Common OU Structure**
- **IT Department** 💻
- **Management** 👔  
- **Marketing** 📢
- **R&D** 🔬
- **Sales** 💰

---

## 🛠️ **Management Tool**
- **Active Directory Users & Computers** 🎛️
- **Create/delete/modify** users & groups 🔧
- **Reset passwords** & manage permissions 🔑

---

## 🎯 **Groups vs OUs**
- **OUs** = Apply **policies** 📋
- **Groups** = Grant **resource permissions** 🔓
- **Users can be in multiple groups** but **only one OU** 🎪

**The backbone of corporate Windows networks!** 😊🏰✨