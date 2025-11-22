### 🔍 Basic Usage

- `find PATH -name PATTERN` → Search for files in PATH matching PATTERN

---

### 🎯 Name & Type Matching

- 🆎 `-name "*.txt"` → Match by filename (case-sensitive)
- 🆎 `-iname "*.txt"` → Match by filename (ignore case)
- 📂 `-type d` → Find directories only
- 📄 `-type f` → Find files only
- 🔗 `-type l` → Find symbolic links

---

### 📏 Size & Time

- 📦 `-size +10M` → Files larger than 10 MB
- 📦 `-size -1k` → Files smaller than 1 KB
- ⏰ `-mtime -7` → Modified in last 7 days
- ⏰ `-atime +30` → Accessed more than 30 days ago

---

### ⚙️ Actions

- 🖨️ `-print` → Show results (default)
- 🗑️ `-delete` → Delete found files (⚠️ careful!)
- 🛠️ `-exec CMD {} \;` → Run command on each result
- 🛠️ `-exec CMD {} +` → Run command on _all_ results at once

---

### 📍 Filtering

- 👤 `-user USER` → Files owned by USER
- 👥 `-group GROUP` → Files owned by GROUP
- 🔒 `-perm 644` → Files with exact permissions
- 🔒 `-perm -u+x` → Files where user has execute permission

---

### 🧪 Examples

```bash
find . -name "*.log"          # 🔍 Find all .log files in current dir
find /etc -type d             # 📂 Find directories under /etc
find . -size +100M -delete    # 🗑️ Delete files >100MB
find . -mtime -1 -exec ls -l {} \;   # ⏰ List files modified today
find /home -user enver        # 👤 Find files owned by user "enver"
```

---

⚡ **Pro tip:** Combine filters!  
Example:  
`find /var/log -type f -size +1M -mtime -7 -exec gzip {} \;` → Find log files >1MB modified in last week, compress them 📦.