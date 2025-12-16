Attackers rarely try to break encryption directly—it’s too slow with modern cryptography. Instead, they guess the password protecting the file. The two main methods are **dictionary attacks** and **brute‑force/mask attacks**.

---

## 📖 Dictionary Attacks

- Use a **wordlist** (predefined set of passwords).
- Wordlists often include:
    - Leaked passwords from breaches
    - Common substitutions (e.g., `password123`)
    - Names, dates, and predictable patterns
- **Why effective?** Many users pick weak, common passwords → fast wins for attackers.

---

## 🧮 Brute‑Force Attacks

- Try **every possible combination** of characters.
- Guaranteed success eventually, but time grows **exponentially** with password length and complexity.
- Example: a 10‑character password with mixed symbols could take years to crack.

---

## 🎭 Mask Attacks

- A smarter version of brute‑force.
- Restrict guesses to a **specific format** (e.g., `?l?l?l?d?d` → three lowercase letters + two digits).
- **Benefit:** Narrows the search space → faster, especially if attacker knows likely structure.

---

## 🛠 Practical Tips (Used by Attackers, Useful for Defenders)

- ✅ Start with common wordlists (`rockyou.txt`, `common-passwords.txt`).
- 🎯 Move to **targeted wordlists** (company names, project names, leaked data).
- 🔑 Use **mask/incremental attacks** for short passwords.
- ⚡ Leverage **GPU acceleration** → massive speed boost.
- 👀 Monitor resource usage: cracking is CPU/GPU intensive and can be detected on endpoints.