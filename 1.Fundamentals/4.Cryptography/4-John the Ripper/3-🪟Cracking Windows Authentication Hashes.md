Now that we’ve covered the basics of John the Ripper, let’s move on to a more advanced and realistic scenario: **cracking Windows authentication hashes**. These are hashed versions of passwords stored by operating systems. While not always necessary, cracking them can be useful during **penetration tests** or **red team engagements**.

---

## 🔑 NTHash / NTLM

- **NTHash** is the format modern Windows systems use to store user and service passwords.
- It’s often referred to as **NTLM**, a name that comes from the older **LM (LAN Manager)** hashing scheme. Together, they’re sometimes called **NT/LM**.

---

## 📜 A Bit of History

- The **NT** designation originally stood for _New Technology_.
- It was introduced with **Windows NT**, which was the first Microsoft OS not built on MS-DOS.
- Over time, NT became the standard Windows architecture, and the branding was dropped—though the name still survives in technologies like **NTFS** and **NTLM**.

---

## 🗂️ Where Hashes Are Stored

Windows stores authentication data in specific places:

- **SAM (Security Account Manager):**
    - Contains local user account information, including usernames and password hashes.
- **Active Directory (NTDS.dit):**
    - Stores domain user account information in enterprise environments.

---

## 🛠️ How to Acquire NTHash/NTLM Hashes

- **Dumping the SAM database** on a Windows machine.
- Using tools like **Mimikatz**.
- Extracting from **NTDS.dit** in Active Directory environments.

---

## ⚔️ Cracking vs. Passing the Hash

- **Pass-the-Hash Attack:**
    - You don’t need to crack the password. Instead, you reuse the hash directly to authenticate.
- **Hash Cracking:**
    - Still useful if the organization enforces weak password policies.
    - Allows you to recover the plaintext password, which may be reused across systems.