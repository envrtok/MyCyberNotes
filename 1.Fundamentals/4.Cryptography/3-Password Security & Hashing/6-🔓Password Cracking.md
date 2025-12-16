We’ve already mentioned **rainbow tables** as a method to crack hashes that don’t use a salt. But what happens when a **salt** is involved?

👉 **Important distinction**:

- Password hashes are **not encrypted** — they cannot be “decrypted.”
- Instead, they must be **cracked** by hashing many candidate inputs (e.g., from `rockyou.txt`), optionally adding the salt, and comparing the result to the target hash.
- Once a match is found, the original password is revealed.

Common cracking tools:

- **Hashcat**
- **John the Ripper**

---

## ⚡ Cracking with GPUs

- **GPUs** have thousands of cores, optimized for parallel mathematical operations.
- They excel at the repetitive calculations used in hash functions.
- This makes them ideal for cracking many hash types quickly.

⚠️ Some algorithms are **GPU-resistant**:

- **Bcrypt** is intentionally designed so GPU acceleration offers little to no speed advantage.
- This makes it harder to crack compared to MD5, SHA1, or NTLM.

---

## 🖥️ Cracking on Virtual Machines (VMs)

- VMs typically **don’t have direct access to the host GPU**.
- GPU passthrough can be configured, but it’s complex and performance suffers.
- CPU performance also degrades in virtualized environments, which is critical since cracking requires maximum efficiency.

### Recommendations

- Run **Hashcat** directly on the host OS to leverage GPU power.
- On **Windows**, Hashcat builds are available and can be run from PowerShell.
- Hashcat can run in a VM with OpenCL, but expect slower speeds.
- **John the Ripper** uses CPU by default and works fine in a VM, though performance is better on the host OS.

---

## 🛠️ Hashcat Basics

Hashcat syntax:

```
hashcat -m <hash_type> -a <attack_mode> hashfile wordlist
```

### Parameters

- `-m <hash_type>` → numeric code for the hash type
    - Example: `-m 1000` = NTLM
- `-a <attack_mode>` → attack mode
    - Example: `-a 0` = straight (wordlist attack)
- `hashfile` → file containing the target hash(es)
- `wordlist` → dictionary file (e.g., `rockyou.txt`)

### Example

```
hashcat -m 3200 -a 0 hash.txt /usr/share/wordlists/rockyou.txt
```

- Treats the hash as **Bcrypt** (`-m 3200`)
- Uses a **straight wordlist attack** (`-a 0`)
- Tests each password in `rockyou.txt` against the hash in `hash.txt`

---

## 🧩 Practical Workflow

1. **Identify the hash type** (prefix, length, context, or using tools like `hashID`).
2. **Select the right Hashcat mode** (`-m`).
3. **Choose attack mode** (`-a`):
    - `0` → straight wordlist
    - `3` → brute-force mask attack
    - `6/7` → hybrid attacks (wordlist + mask)
4. **Run with a strong wordlist** (e.g., `rockyou.txt`).
5. **Monitor performance** (GPU vs CPU, host vs VM).