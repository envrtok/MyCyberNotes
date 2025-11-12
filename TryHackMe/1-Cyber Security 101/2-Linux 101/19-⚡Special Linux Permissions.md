## 👑 SUID (Set User ID)

**What it is:**
- A special permission that makes a program run as the **file owner** instead of the user running it
- **Normally**: You run a program with **your** permissions
- **With SUID**: You run a program with the **owner's** permissions

**How to find SUID files:**
```bash
find / -perm -u=s -type f 2>/dev/null
```
- This searches the entire system for files with SUID set
- `2>/dev/null` hides error messages for directories you can't access

**How it looks in `ls -l`:**
```
-rwsr-xr-x 1 root root  /usr/bin/passwd
```
- The **`s`** in the owner's execute position (`rws` instead of `rwx`)
- Normal: `-rwxr-xr-x`
- SUID: `-rwsr-xr-x`

**Why it's a security risk:**
- If a hacker finds a vulnerable SUID program owned by root, they can exploit it to become root
- Example: If `/usr/bin/vim` had SUID and was owned by root, anyone could edit any system file

**Common legitimate SUID examples:**
- `passwd` - Needs to edit /etc/shadow (root-only file)
- `sudo` - Needs to run commands as other users

---

### 👥 SGID (Set Group ID)

**What it is:**
- Makes a program run with the **file's group** permissions
- When used on directories: New files inherit the directory's group

**How to find SGID files:**
```bash
find / -perm -g=s -type f 2>/dev/null
```

**How it looks in `ls -l`:**
```
-rwxr-sr-x 1 root staff  /usr/local/bin/special-program
```
- The **`s`** in the group's execute position (`r-s` instead of `r-x`)

**SGID on directories:**
```
drwxr-sr-x 2 root developers  /shared-project
```
- Any file created in this directory gets the `developers` group
- Useful for team collaboration

---

### 📌 Sticky Bit

**What it is:**
- A special permission that **protects files in shared directories**
- Only the **file owner** (or root) can delete or rename their own files
- Prevents users from deleting each other's files in shared spaces

**Where you'll find it:**
- `/tmp` - Temporary files directory
- `/var/tmp` - Another temporary directory

**How it looks in `ls -l`:**
```
drwxrwxrwt 10 root root  /tmp
```
- The **`t`** in the others' execute position (`rwt` instead of `rwx`)
- Normal directory: `drwxrwxrwx`
- Sticky bit: `drwxrwxrwt`

**How it works:**
- In `/tmp`, UserA creates File1, UserB creates File2
- UserB **cannot** delete UserA's File1 (and vice versa)
- Only UserA or root can delete File1

---

## 👑 File Ownership with `chown`

### 🔧 Changing File Ownership
**`chown`** = **Change Owner** - controls who owns files/directories

**Basic Syntax:**
```bash
chown newowner filename
chown newowner:newgroup filename
```

### 🛠️ `chown` Examples

**Change file owner:**
```bash
chown alice document.txt          # Now alice owns document.txt
chown bob /shared/folder/         # bob owns the folder
```

**Change owner AND group:**
```bash
chown alice:developers script.sh  # alice owns, developers group
chown :www-data website/          # Change only group to www-data
```

**Recursive ownership changes:**
```bash
chown -R alice:alice /home/alice/ # Change everything in alice's home
chown -R www-data:www-data /var/www/  # Web directory ownership
```

**Reference another file's ownership:**
```bash
chown --reference=source.txt target.txt  # Copy ownership from source
```

### 🔐 Common `chown` Scenarios

**Web Server Setup:**
```bash
# Make web files owned by web server user
sudo chown -R www-data:www-data /var/www/html/
```

**User Home Directory:**
```bash
# Fix ownership after system restore
sudo chown -R username:username /home/username/
```

**Shared Project Directory:**
```bash
# Set up shared workspace with SGID
sudo chown root:developers /shared-project
sudo chmod 2775 /shared-project    # SGID + rwx for owner/group
```

---

## 🛠️ Setting Special Permissions

**Set SUID:**
```bash
chmod u+s filename
chmod 4755 filename    # 4 = SUID
```

**Set SGID:**
```bash
chmod g+s filename
chmod 2755 filename    # 2 = SGID
```

**Set Sticky Bit:**
```bash
chmod +t directoryname
chmod 1777 directoryname    # 1 = Sticky bit
```

### 🔧 Combined Examples

**Secure Shared Directory:**
```bash
# Create shared space where users can't delete each other's files
sudo mkdir /shared-workspace
sudo chown root:team /shared-workspace
sudo chmod 1777 /shared-workspace    # Sticky bit + full permissions
```

**SUID Program Setup:**
```bash
# Make a script run as root (use carefully!)
sudo chown root:root /usr/local/bin/admin-tool
sudo chmod 4755 /usr/local/bin/admin-tool    # SUID + rwxr-xr-x
```

**SGID Collaboration Directory:**
```bash
# Files inherit group ownership automatically
sudo chown root:developers /team-projects
sudo chmod 2775 /team-projects    # SGID + rwx for owner/group
```

---

## 🔍 Security Check Examples

```bash
# Find all SUID files (potential security risks)
find / -perm -u=s -type f 2>/dev/null

# Find all SGID files
find / -perm -g=s -type f 2>/dev/null

# Find directories with sticky bit
find / -perm -1000 -type d 2>/dev/null

# Check ownership of sensitive directories
ls -la /etc/passwd /etc/shadow /tmp /var/tmp
```

### ⚠️ Security Best Practices

**Dangerous Combinations:**
- **SUID + world-writable** = Major security risk 🚨
- **SGID on sensitive programs** = Potential privilege escalation
- **Wrong ownership on system files** = System instability

**Safe Practices:**
- Use `chown` carefully - wrong ownership can break system functions
- Limit SUID/SGID programs to essential system tools only
- Regular security audits with `find` commands above
- Understand the purpose before changing permissions/ownership

These tools give you complete control over file security and sharing on Linux! 🔐✨