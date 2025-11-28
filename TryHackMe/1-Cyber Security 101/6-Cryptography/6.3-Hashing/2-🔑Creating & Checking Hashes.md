### 🔑 Common Hash Commands in Linux

| Algorithm   | Command Example      | Notes (hex)                               |
| ----------- | -------------------- | ----------------------------------------- |
| **MD5**     | `md5sum file.txt`    | Produces a 32‑character hash.             |
| **SHA‑1**   | `sha1sum file.txt`   | 40‑character hash, older and less secure. |
| **SHA‑256** | `sha256sum file.txt` | 64‑character hash, widely used today.     |
| **SHA‑512** | `sha512sum file.txt` | 128‑character hash, stronger but longer.  |

---

### 📌 Usage

- Replace `file.txt` with the path to your file.
- Example:
    
    ```bash
    md5sum mydocument.pdf
    sha256sum mydocument.pdf
    sha512sum mydocument.pdf
    ```
    
- Output looks like:
    
    ```
    d41d8cd98f00b204e9800998ecf8427e  mydocument.pdf
    ```
    

---

### ⚙️ Verify File Integrity

If you have a checksum file (e.g., `file.txt.sha256`), you can verify:

```bash
sha256sum -c file.txt.sha256
```

This checks whether the file’s hash matches the expected one.

---

### 🛠️ Extra Tools

- **`openssl`** can also generate hashes:
    
    ```bash
    openssl dgst -sha256 file.txt
    openssl dgst -md5 file.txt
    ```
    
- **`b2sum`** → for BLAKE2 hashes (modern, fast alternative).