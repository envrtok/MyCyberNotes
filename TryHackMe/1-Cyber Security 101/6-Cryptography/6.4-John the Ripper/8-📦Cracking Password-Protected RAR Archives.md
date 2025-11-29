RAR archives (created with **WinRAR**) are compressed files similar to ZIP archives. If they’re password-protected, John the Ripper can be used to crack them by first converting the archive into a hash format John understands.

---

## 🔄 Rar2John

The **`rar2john`** tool extracts password hashes from RAR files and outputs them in a format John can process.

**Syntax:**

```
rar2john [rar file] > [output file]
```

- **rar2john** → Invokes the tool
- **[rar file]** → Path to the RAR archive you want to crack
- **`>`** → Redirects output to a file
- **[output file]** → File that stores the extracted hash

**Example:**

```
/opt/john/rar2john rarfile.rar > rar_hash.txt
```

---

## 🛠️ Cracking the Hash

Once you’ve generated the hash file (`rar_hash.txt`), feed it into John:

**Basic usage:**

```
john --wordlist=/usr/share/wordlists/rockyou.txt rar_hash.txt
```

- `--wordlist=` → Specifies the dictionary file (e.g., `rockyou.txt`)
- `rar_hash.txt` → The hash file created by `rar2john`

John will then attempt to crack the RAR password using the supplied wordlist.

---

## 🔑 Workflow Summary

1. Run `rar2john` on the target RAR file.
2. Save the output hash to a file (e.g., `rar_hash.txt`).
3. Run John with a wordlist against the hash file.
4. If successful, John reveals the RAR password.

---

✅ This version makes the process easy to follow: **extract → convert → crack**.