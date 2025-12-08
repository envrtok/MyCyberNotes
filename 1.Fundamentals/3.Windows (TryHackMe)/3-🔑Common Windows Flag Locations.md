### 1. **System Root (`C:\`)**

- Why: It’s the first place you land after compromise.
- Typical flag: `flag{access_the_machine}` or similar.
- Real-world analogy: Attackers often drop or find indicators here because it’s universally accessible.

---

### 2. **Password Storage (`C:\Windows\System32\config\SAM`)**

- Why: SAM holds local account password hashes.
- Typical flag: Hidden inside or near the SAM file.
- Real-world analogy: Credential dumping targets SAM + SYSTEM hive to extract NTLM hashes.

---

### 3. **Administrator Profile (`C:\Users\Administrator\Desktop` or `Documents`)**

- Why: Admins usually store sensitive files here.
- Typical flag: `flag3.txt` or loot-style files.
- Real-world analogy: Attackers check admin profiles for saved credentials, configs, or scripts.

---

### 4. **ProgramData / AppData**

- Why: Applications stash configs, cached credentials, or temp files.
- Typical flag: Sometimes hidden in `C:\ProgramData` or `C:\Users\<User>\AppData\Roaming`.
- Real-world analogy: Persistence mechanisms and malware often hide here.

---

### 5. **Registry Hives**

- Why: Registry contains system secrets (e.g., LSA secrets, cached credentials).
- Typical flag: Could be embedded in `HKLM\SAM` or `HKLM\Security`.
- Real-world analogy: Tools like Mimikatz pull credentials directly from LSASS/registry.

---

### 6. **Temp / Recycle Bin**

- Why: Easy to overlook, but often writable by all users.
- Typical flag: Dropped in `C:\Windows\Temp` or `$Recycle.Bin`.
- Real-world analogy: Attackers use these for staging payloads or hiding artifacts.

---

## 🎯 Why CTFs Use These Spots

- They teach you **where attackers look in real compromises**.
- Each flag location corresponds to a **real post-exploitation technique**:
    - Root → initial access.
    - SAM → credential dumping.
    - Admin profile → looting.
    - ProgramData/AppData → persistence.
    - Registry → secrets.
    - Temp/Recycle Bin → staging.