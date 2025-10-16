## **🔍 Searching by Name**

| Command | Description | Example |
| :--- | :--- | :--- |
| `find (path) -name (pattern)` | Searchs all file and gives the file with given name 🔦 | `find . -name myfile.txt` 📄 |
| `find (path) -iname (pattern)` | Same with -name, without case sensetive 🅰️🅱️ | `find . -iname MyFile.TXT` 🔤 |
| `find (path) -path (*/pattern/*)` | Searches the entire path for the pattern. Finds any item located **inside** a directory whose name matches pattern. 📂 | `find . -path */myfolder/*` 🗂️ |

---

## **📁 Searching by Type**

| **Option** | **Description** | **Example** |
| :--- | :--- | :--- |
| `-type f` | Searches for regular files 📄 | `find /home -type f` 🏠 |
| `-type d` | Searches for directories 📂 | `find . -type d` 📁 |
| `-type l` | Searches for symbolic links 🔗 | `find /usr -type l` ⚡ |

---

## **⏰ Searching by Time**

| **Option** | **Description** | **Example** |
| :--- | :--- | :--- |
| `-mtime [n]` | Finds files that were last modified `n` days ago 📅 | `find . -mtime -7` (last 7 days) 🆕 |
| `-atime [n]` | Finds files that were last accessed `n` days ago 👀 | `find /var/log -atime +30` (over 30 days) 🗑️ |
| `-ctime [n]` | Finds files whose status was last changed `n` days ago 🔄 | `find . -ctime 1` (exactly 1 day) ⏳ |
| `-mmin [n]` | Finds files last modified `n` minutes ago ⏱️ | `find . -mmin -60` (last hour) 🕐 |

---

## **📏 Searching by Size**

| **Option** | **Description** | **Example** |
| :--- | :--- | :--- |
| `-size [n]c` | Finds files that are exactly `n` bytes in size 🔢 | `find . -size 1024c` (exactly 1KB) 📊 |
| `-size +[n]k` | Finds files larger than `n` kilobytes 📈 | `find /var -size +100M` (over 100MB) 🚀 |
| `-size -[n]M` | Finds files smaller than `n` megabytes 📉 | `find . -size -10k` (under 10KB) 📥 |
| `-empty` | Finds empty files and directories 🫗 | `find . -type f -empty` 🎯 |

---

## **🔐 Searching by Permissions & Ownership**

| **Option** | **Description** | **Example** |
| :--- | :--- | :--- |
| `-user [username]` | Finds files owned by the specified user 👤 | `find . -user john` 👨‍💻 |
| `-group [groupname]` | Finds files belonging to the specified group 👥 | `find /etc -group admin` 🛡️ |
| `-perm [mode]` | Finds files with the specified permissions 🔒 | `find . -perm 644` (rw-r--r--) 📋 |

---