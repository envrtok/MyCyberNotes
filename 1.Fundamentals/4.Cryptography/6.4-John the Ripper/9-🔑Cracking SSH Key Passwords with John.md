In Capture the Flag (CTF) challenges and penetration tests, you may encounter **SSH private keys (`id_rsa`)** protected by a passphrase. To use the key for authentication, you must first unlock it with the correct password. John the Ripper can help crack these passphrases.

---

## 🔄 SSH2John

Like other conversion tools in the John suite, **`ssh2john`** converts an SSH private key into a hash format that John can process.

**Syntax:**

```
ssh2john [id_rsa private key file] > [output file]
```

- **ssh2john** → Invokes the tool
- **[id_rsa private key file]** → Path to the private key file
- **`>`** → Redirects output to a file
- **[output file]** → File that stores the extracted hash

**Example:**

```
/opt/john/ssh2john.py id_rsa > id_rsa_hash.txt
```

> 💡 Note: If `ssh2john` isn’t installed, use the Python script version:
> 
> - On AttackBox: `python3 /opt/john/ssh2john.py id_rsa > id_rsa_hash.txt`
> - On Kali: `python /usr/share/john/ssh2john.py id_rsa > id_rsa_hash.txt`

---

## 🛠️ Cracking the Hash

Once you’ve generated the hash file (`id_rsa_hash.txt`), feed it into John:

**Basic usage:**

```
john --wordlist=/usr/share/wordlists/rockyou.txt id_rsa_hash.txt
```

- `--wordlist=` → Specifies the dictionary file (e.g., `rockyou.txt`)
- `id_rsa_hash.txt` → The hash file created by `ssh2john`

John will then attempt to crack the SSH key passphrase using the supplied wordlist.

---

## 🔑 Workflow Summary

1. Extract the hash from the private key using `ssh2john`.
2. Save the output to a file (e.g., `id_rsa_hash.txt`).
3. Run John with a wordlist against the hash file.
4. If successful, John reveals the passphrase, allowing you to unlock the SSH key.

---

✅ This version makes the process clear: **convert → hash → crack → unlock**.