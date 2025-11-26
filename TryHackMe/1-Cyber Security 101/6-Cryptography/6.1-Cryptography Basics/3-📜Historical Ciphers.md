Cryptography dates back to **ancient Egypt (1900 BCE)**.  
Early ciphers were simple substitution or transposition methods, designed to obscure messages.

---

## ✨ Caesar Cipher (1st Century BCE)

- **Idea** → shift each letter by a fixed number.
- Example:
    - Plaintext: `TRYHACKME`
    - Key: `3` (right shift)
    - Ciphertext: `WUBKDFNPH`
- **Encryption** → shift right by key value.
- **Decryption** → shift left by key value.
- **Weakness** → only 25 possible keys → trivial brute force.
- **Status today** → insecure, but foundational for learning.

---

## 🧩 Other Historical Ciphers

- **Vigenère Cipher (16th century)**
    
    - Uses a keyword to apply multiple Caesar shifts.
    - More resistant than Caesar, but still breakable with modern analysis.
- **Enigma Machine (WWII)**
    
    - Electromechanical rotor-based cipher used by Germany.
    - Broken by Allied cryptanalysts (notably at Bletchley Park).
- **One-Time Pad (Cold War)**
    
    - Uses a truly random key as long as the message.
    - If used correctly → **perfect secrecy** (unbreakable).
    - Impractical due to key distribution challenges.

---

## 📊 Quick Recap Table

|Cipher|Era|Method|Security Today|
|---|---|---|---|
|Caesar|1st Century BCE|Shift letters|Insecure|
|Vigenère|16th Century|Keyword shifts|Weak|
|Enigma|WWII|Rotor machine|Broken|
|One-Time Pad|Cold War|Random key|Perfect (if used correctly)|

---

# 🎯 Takeaway

Historical ciphers laid the foundation for **modern cryptography**.

- Caesar → simple substitution
- Vigenère → polyalphabetic substitution
- Enigma → mechanical complexity
- One-Time Pad → theoretical perfection

They illustrate the **evolution from simplicity to sophistication**, and why modern cryptography relies on **mathematics + computing power** rather than secrecy of the method.