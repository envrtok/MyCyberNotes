## 🔎 Purpose

- `hashdump` extracts **password hashes** from the Windows **SAM database**.
- Useful for retrieving NTLM hashes of local user accounts (e.g., `pirate`).
- Requires **SYSTEM privileges** (which you already have via EternalBlue).

---

## ⚙️ Command

```bash
meterpreter > hashdump
```

---

## 📂 Output Format

Each line follows this structure:

```
username:RID:LM_hash:NTLM_hash
```

### Field Breakdown

|Field|Meaning|Example|
|---|---|---|
|`username`|Account name|`pirate`|
|`RID`|Relative Identifier (unique per user)|`1001`|
|`LM_hash`|Legacy LAN Manager hash (often disabled, shows as `aad3b435b51404eeaad3b435b51404ee`)|`aad3b435b51404eeaad3b435b51404ee`|
|`NTLM_hash`|Modern hash of the password (the one you need in CTFs)|`8846f7eaee8fb117ad06bdd830b7586c`|

---

## 🛠 Workflow

1. **Run the command**
    
    ```bash
    hashdump
    ```
    
2. **Locate the target user**  
    Find the line with `pirate`.
3. **Extract the NTLM hash**  
    Copy the **fourth field** (long hex string).
4. **Use the hash in CTF**
    - Submit it as the flag.
    - Or crack it with tools like `john` or `hashcat` if required.

---

## ⚠️ Notes

- LM hashes are usually disabled; ignore them.
- NTLM hashes are case‑insensitive hex strings.
- In real environments, dumping hashes is sensitive and requires explicit permission. In CTFs, it’s safe and expected.

---

## 🧩 Example

```
pirate:1001:aad3b435b51404eeaad3b435b51404ee:8846f7eaee8fb117ad06bdd830b7586c
```

👉 The NTLM hash of `pirate` is:

```
8846f7eaee8fb117ad06bdd830b7586c
```