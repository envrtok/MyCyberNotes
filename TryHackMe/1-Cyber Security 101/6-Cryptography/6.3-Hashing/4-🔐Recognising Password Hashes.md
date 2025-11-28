From a **defensive security** perspective, we’ve already covered how to store passwords securely for authentication systems. Now let’s flip to the **offensive security** side:

👉 If we start with a hash, how can we recognise its type, crack it, and recover the original password?

---

## ⚙️ Hash Recognition

- **Automated tools** like `hashID` can identify hash types, but they’re not always reliable.
- **Prefixes** (e.g., `$y$`, `$6$`) make recognition easier, and tools handle these well.
- **Context matters**:
    - A hash found in a **web app database** is more likely **MD5** than **NTLM**.
    - Tools often confuse MD5, MD4, and NTLM, so learning to recognise them yourself is essential.

---

## 🐧 Linux Passwords

- Password hashes are stored in **`/etc/shadow`** (readable only by root).
- Historically, they were in **`/etc/passwd`**, which was world-readable.

### Shadow File Structure

- Each line has **9 fields**, separated by colons (`:`).
- The **first two fields**:
    - **Login name**
    - **Encrypted password**

For details on other fields: run `man 5 shadow`.

### Encrypted Password Format

Stored as:

```
$prefix$options$salt$hash
```

- **Prefix** → algorithm identifier
- **Options** → parameters
- **Salt** → random value to strengthen the hash
- **Hash** → final hashed password

---

## 📑 Common Unix Password Prefixes

|Prefix|Algorithm|Notes|
|---|---|---|
|`$y$`|yescrypt|Default in modern systems; scalable and recommended|
|`$gy$`|gost-yescrypt|Uses GOST R 34.11-2012 + yescrypt|
|`$7$`|scrypt|Password-based key derivation function|
|`$2b$, $2y$, $2a$, $2x$`|bcrypt|Based on Blowfish; widely supported across Unix-like systems|
|`$6$`|sha512crypt|SHA-512 based; common in older Linux systems|
|`$md5`|SunMD5|Solaris-specific MD5 variant|
|`$1$`|md5crypt|FreeBSD’s MD5-based hash|

---

## 🖥️ Modern Linux Example

Example line from `/etc/shadow`:

```
strategos:$y$j9T$76UzfgEM5PnymhQ7TlJey1$/OOSg64dhfF.TigVPdzqiFang6uZA4QA1pzzegKdVm4:19965:0:99999:7:::
```

Breaking down the **second field** (`$y$j9T$76UzfgEM5PnymhQ7TlJey1$/OOSg64dhfF...`):

- `y` → algorithm = **yescrypt**
- `j9T` → parameter passed to algorithm
- `76UzfgEM5PnymhQ7TlJey1` → **salt**
- `/OOSg64dhfF...` → **hash value**

---

## 🪟 Windows Passwords

- Windows uses **NTLM**, a variant of **MD4**.
- NTLM hashes look visually similar to MD4 and MD5 → context is critical for recognition.

### Storage

- Password hashes are stored in the **SAM (Security Accounts Manager)**.
- Windows restricts access, but tools like **Mimikatz** can extract them.
- Two types of hashes:
    - **NT hashes**
    - **LM hashes**

---

## 📚 Further Resources

- **Hashcat Example Hashes** → excellent reference for hash formats and prefixes.
- For other hash types:
    - Check **length**
    - Check **encoding**
    - Research the **application** that generated the hash

👉 Never underestimate the power of **research**.