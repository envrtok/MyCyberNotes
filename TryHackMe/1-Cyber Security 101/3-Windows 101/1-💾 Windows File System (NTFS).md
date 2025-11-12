### 📁 File System Types
- **NTFS** (New Technology File System) - Modern Windows file system
- **FAT16/FAT32** - Older file systems, still used in USB drives and memory cards
- **HPFS** - High Performance File System (historical)

### ⭐ NTFS Key Features
- **Journaling**: Automatically repairs files after system crashes 📝
- **Large file support**: Files larger than 4GB 💾
- **Permissions**: Control access to files and folders 🔐
- **Compression**: Reduce file size automatically 🗜️
- **Encryption**: EFS (Encryption File System) for security 🔒

### 🔐 NTFS Permissions
**Basic Permissions:**
- **Full control** - Complete access (read, write, delete, change permissions)
- **Modify** - Read, write, and delete files/folders
- **Read & Execute** - View and run programs
- **List folder contents** - See files in folders
- **Read** - View files only
- **Write** - Create and modify files

**How to Check Permissions:**
1. Right-click file/folder → **Properties**
2. Click **Security** tab
3. Select user/group to see their permissions

### 🕵️ Alternate Data Streams (ADS)
- **Hidden data streams** in NTFS files
- **Normal files** have one data stream (`$DATA`)
- **ADS files** can have multiple hidden data streams
- **Security concern**: Malware can hide in ADS
- **Legitimate use**: Marks downloaded files from internet

**Viewing ADS in PowerShell:**
```powershell
Get-Item filename -stream *
```

### 🔍 Practical Information
- **Check your file system**: Right-click C: drive → Properties
- **Most Windows computers use NTFS**
- **External devices often use FAT32** for compatibility

NTFS provides strong security and reliability for modern Windows systems! 🛡️