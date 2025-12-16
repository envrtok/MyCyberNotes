## 1️⃣ Identify File Type

Before choosing a tool, confirm the file type:

```bash
file flag.pdf
file flag.zip
```

- **PDF** → use PDF‑specific cracking tools.
- **ZIP** → use ZIP‑specific cracking tools.
- **General** → flexible tools like `john` or `hashcat`.

---

## 2️⃣ Tools: What They Do, Why They’re Used, and Example Commands

- **pdfcrack** → Specialized for PDFs. Directly tests passwords.  
    _Why:_ Lightweight, quick dictionary attacks.
    
    ```bash
    pdfcrack -f flag.pdf -w /usr/share/wordlists/rockyou.txt
    ```
    
- **pdf2john + john** → Convert PDF to hash, then crack with John.  
    _Why:_ More flexible, supports advanced modes.
    
    ```bash
    pdf2john flag.pdf > pdfhash.txt
    john --wordlist=/usr/share/wordlists/rockyou.txt pdfhash.txt
    ```
    
- **fcrackzip** → Designed for ZIP archives.  
    _Why:_ Simple, effective for quick dictionary attacks.
    
    ```bash
    fcrackzip -u -D -p /usr/share/wordlists/rockyou.txt flag.zip
    ```
    
- **zip2john + john** → Convert ZIP to hash, then crack with John.  
    _Why:_ Enables advanced strategies with John.
    
    ```bash
    zip2john flag.zip > ziphash.txt
    john --wordlist=/usr/share/wordlists/rockyou.txt ziphash.txt
    ```
    
- **john (John the Ripper)** → General‑purpose cracker.  
    _Why:_ Versatile, supports many formats, dictionary, mask, brute‑force.
    
    ```bash
    john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
    ```
    
- **hashcat** → GPU‑accelerated cracker.  
    _Why:_ Extremely fast for large search spaces.
    
    ```bash
    hashcat -m 10500 hash.txt /usr/share/wordlists/rockyou.txt
    ```
    

---

## 3️⃣ Attack Strategies: How They Work and Example Commands

### 📖 Dictionary Attack

- **What:** Test passwords from a wordlist.
- **Why:** Fast, effective because users often pick weak/common passwords.
- **Example (PDF with pdfcrack):**
    
    ```bash
    pdfcrack -f flag.pdf -w /usr/share/wordlists/rockyou.txt
    ```
    

### 🧮 Brute‑Force Attack

- **What:** Try every possible combination of characters.
- **Why:** Guaranteed success, but time grows exponentially with length/complexity.
- **Example (ZIP with fcrackzip):**
    
    ```bash
    fcrackzip -u -b -c aA1 flag.zip
    ```
    
    _(tries all lowercase, uppercase, and digits)_

### 🎭 Mask Attack

- **What:** Restrict guesses to a format (e.g. `?l?l?l?d?d`).
- **Why:** Narrows search space, balances speed and coverage.
- **Example (Hashcat mask attack):**
    
    ```bash
    hashcat -m 10500 hash.txt -a 3 ?l?l?l?d?d
    ```
    
    _(three lowercase letters + two digits)_

---

## 4️⃣ Practical Workflow

1. **Identify file type** → PDF or ZIP.
2. **Pick tool** → pdfcrack/pdf2john for PDF, fcrackzip/zip2john for ZIP.
3. **Run dictionary attack** → start with common wordlists (`rockyou.txt`).
4. **Escalate** → targeted wordlists (names, projects, leaked data).
5. **Mask attacks** → apply structured guesses for short passwords.
6. **Brute‑force** → only if all else fails.
7. **GPU acceleration** → use hashcat for speed.
8. **Monitor system resources** → cracking is CPU/GPU intensive, detectable on endpoints.

---

## 🧩 Key Takeaways

- Tools exist because encryption is strong — attackers exploit weak passwords instead.
- Dictionary attacks succeed quickly due to human predictability.
- Mask attacks are efficient when structure is known.
- Brute‑force is slow but inevitable if password is short/simple.
- Defenders should enforce strong, complex passwords and monitor for cracking behavior.