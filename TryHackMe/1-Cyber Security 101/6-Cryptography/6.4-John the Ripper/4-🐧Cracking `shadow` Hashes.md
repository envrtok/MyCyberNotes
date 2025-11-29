On Linux systems, password hashes are stored in the **`/etc/shadow`** file. This file also contains metadata such as the date of the last password change and expiration information. Each line corresponds to a user account.

⚠️ Access is restricted: only the **root user** can read `/etc/shadow`. If you gain sufficient privileges, you may be able to extract and crack these hashes.

---

## 🔄 Unshadowing

John the Ripper requires a specific format to work with `/etc/shadow` hashes. To prepare the data, you must combine `/etc/passwd` with `/etc/shadow` using the **`unshadow`** tool (included with John).

**Syntax:**

```
unshadow [path to passwd] [path to shadow]
```

- **unshadow** → Invokes the tool
- **[path to passwd]** → Copy of `/etc/passwd` from the target machine
- **[path to shadow]** → Copy of `/etc/shadow` from the target machine

**Example:**

```
unshadow local_passwd local_shadow > unshadowed.txt
```

---

## 📂 Notes on Files

You can use either:

- The **entire `/etc/passwd` and `/etc/shadow` files**, or
- Just the relevant lines for the user you want to crack.

**Example:**

- `local_passwd` (root user entry):
    
    ```
    root:x:0:0::/root:/bin/bash
    ```
    
- `local_shadow` (root user hash entry):
    
    ```
    root:$6$2nwjN454g.dv4HN/$m9Z/r2xVfweYVkrr.v5Ft8Ws3/YYksfNwq96UL1FX0OJjY1L6l.DS3KEVsZ9rOVLB/ldTeEL/OIhJZ4GMFMGA0:18576::::::
    ```
    

---

## 🛠️ Cracking the Hashes

Once combined, feed the **unshadowed file** into John:

**Basic usage:**

```
john unshadowed.txt
```

**With wordlist and format specified:**

```
john --wordlist=/usr/share/wordlists/rockyou.txt --format=sha512crypt unshadowed.txt
```

- `--wordlist=` → Uses dictionary attack with the specified wordlist
- `--format=sha512crypt` → Explicitly tells John the hash type (sometimes required)

---

## 🔑 Workflow Summary

1. Extract `/etc/passwd` and `/etc/shadow` from the target system.
2. Combine them with `unshadow`.
3. Save the output (e.g., `unshadowed.txt`).
4. Run John the Ripper with a wordlist (and format if needed).

---

✅ This version makes the process easy to follow: **extract → combine → crack**.