A practical shell script that combines **variables**, **loops**, and **conditional statements** to authenticate a user before granting access to a locker.

---

## 📋 Requirement

- Script must ask for:
    - 👤 **Username** → `John`
    - 🏢 **Company name** → `Tryhackme`
    - 🔢 **PIN** → `7385`
- If all match → ✅ Access granted
- Else → ❌ Access denied

---

## 🖥️ Script Structure

```bash
#!/bin/bash   # Interpreter

# Variables
username=""
companyname=""
pin=""

# Loop (3 inputs)
for i in {1..3}; do
    if [ "$i" -eq 1 ]; then
        echo "Enter your Username:"
        read username
    elif [ "$i" -eq 2 ]; then
        echo "Enter your Company name:"
        read companyname
    else
        echo "Enter your PIN:"
        read pin
    fi
done

# Conditional check
if [ "$username" = "John" ] && [ "$companyname" = "Tryhackme" ] && [ "$pin" = "7385" ]; then
    echo "Authentication Successful. You can now access your locker, John."
else
    echo "Authentication Denied!!"
fi
```

---

## ⚙️ Key Components

- **Variables** 🗂️ → store user input (`username`, `companyname`, `pin`)
- **Loop** 🔁 → iterates 3 times to collect all inputs
- **Conditionals** ⚖️ → check if all inputs match required values
- **Logical AND (`&&`)** → ensures _all three conditions_ must be true

---

## 🧪 Script Execution Example

```bash
user@tryhackme:~$ ./locker_script.sh
Enter your Username:
John
Enter your Company name:
Tryhackme
Enter your PIN:
1349
Authentication Denied!!
```

- Since PIN ≠ `7385` → ❌ Access denied

---

# 📊 Quick Recap Table

|🧩 Component|⚡ Purpose|Example in Script|
|---|---|---|
|**Variable**|Store user input|`read username`|
|**Loop**|Collect multiple inputs|`for i in {1..3}`|
|**Conditional**|Verify correctness of inputs|`if [ "$username" = "John" ] ...`|
|**Logical AND**|Require all conditions true|`&&`|

---

# 🎯 Takeaway

The Locker Script demonstrates how **variables + loops + conditionals** can be combined to build **secure authentication logic** in shell scripting.