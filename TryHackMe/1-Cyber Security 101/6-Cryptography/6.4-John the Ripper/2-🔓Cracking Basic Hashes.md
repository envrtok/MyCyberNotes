There are several ways to use **John the Ripper** to crack simple hashes. Let’s walk through the basics before trying it ourselves.

---

## ⚙️ John Basic Syntax

The general command structure looks like this:

```
john [options] [file path]
```

- **john** → Invokes the John the Ripper program
- **[options]** → Flags or modifiers that control how John runs
- **[file path]** → The file containing the hash(es) you want to crack
    - If the file is in the same directory, just use the filename (no path needed).

---

## 🚀 Automatic Cracking

John can automatically detect the hash type and attempt cracking with default rules. This isn’t always reliable, but it’s useful if you don’t know the hash type.

**Syntax:**

```
john --wordlist=[path to wordlist] [path to file]
```

- `--wordlist=` → Tells John to use dictionary mode
- `[path to wordlist]` → Path to your wordlist file (e.g., `rockyou.txt`)
- `[path to file]` → File containing the hash

**Example:**

```
john --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt
```

---

## 🔍 Identifying Hashes

Sometimes John struggles to recognize hashes automatically. In that case, you can identify the hash type first, then specify it manually.

**Tools for identification:**

- Online hash identifier sites
- **hash-identifier** (Python tool)

**Usage:**

1. Download with `wget` or `curl`:
    
    ```
    wget https://gitlab.com/kalilinux/packages/hash-identifier/-/raw/kali/master/hash-id.py
    ```
    
2. Run with Python:
    
    ```
    python3 hash-id.py
    ```
    
3. Enter your hash → The tool suggests possible formats (e.g., MD5, MD4).

---

## 🎯 Format-Specific Cracking

Once you know the hash type, tell John explicitly:

**Syntax:**

```
john --format=[format] --wordlist=[path to wordlist] [path to file]
```

- `--format=` → Specifies the hash type
- `[format]` → The format name (e.g., `raw-md5`)
- `[path to wordlist]` → Wordlist file
- `[path to file]` → Hash file

**Example:**

```
john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt
```

---
## 🔑 Formats

|Category|Format Names|
|---|---|
|**Classic Unix/Linux**|`descrypt`, `md5crypt`, `sha256crypt`, `sha512crypt`|
|**Windows**|`LM`, `NT`|
|**Raw Hashes**|`raw-MD5`, `raw-SHA1`, `raw-SHA256`, `raw-SHA512`|
|**Modern Algorithms**|`bcrypt`, `scrypt`, `PBKDF2-HMAC-SHA1`, `PBKDF2-HMAC-SHA256`, `PBKDF2-HMAC-SHA512`|
|**Database Hashes**|`MySQL`, `MSSQL`, `Oracle`|
|**File Formats**|`PDF`, `ZIP`, `RAR`, `7z`|
|**Network Protocols**|`WPA-PSK`, `Kerberos`, `NetNTLMv1`, `NetNTLMv2`|
|**Others**|`HMAC-SHA1`, `HMAC-SHA256`, `HMAC-SHA512`, `AIX`|

---
## 📝 Note on Formats

- For standard hash types (like MD5), you often need to prefix with **`raw-`** (e.g., `raw-md5`).
- To check available formats:
    
    ```
    john --list=formats
    ```
    
- To filter for a specific type:
    
    ```
    john --list=formats | grep -iF "md5"
    ```