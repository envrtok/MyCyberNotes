Cryptography transforms **readable data (plaintext)** into **scrambled data (ciphertext)** using a **cipher** and a **key**.  
The reverse process (decryption) restores the original plaintext.

---

## 🧩 Core Terms

- **Plaintext** → original, readable message/data (e.g., “hello”, images, credit card info).
- **Ciphertext** → scrambled, unreadable output after encryption.
- **Cipher** → algorithm that converts plaintext ↔ ciphertext.
- **Key** → secret string of bits used by the cipher for encryption/decryption.
- **Encryption** → process of converting plaintext → ciphertext using cipher + key.
- **Decryption** → process of converting ciphertext → plaintext using cipher + key.

---

## 🔄 Process Flow

1. **Encryption Function**
    
    - Input: plaintext + key
    - Output: ciphertext
2. **Decryption Function**
    
    - Input: ciphertext + key
    - Output: plaintext

👉 Without the correct **key**, recovering plaintext should be **computationally infeasible**.

---

## 📊 Quick Recap Table

|🔑 Term|📌 Definition|
|---|---|
|Plaintext|Original readable data|
|Ciphertext|Scrambled, unreadable data|
|Cipher|Algorithm for encryption/decryption|
|Key|Secret bits used by cipher|
|Encryption|Plaintext → Ciphertext|
|Decryption|Ciphertext → Plaintext|

---

# 🎯 Takeaway

Cryptography relies on **public algorithms (ciphers)** but **secret keys**.  
The strength of encryption lies in keeping the **key hidden**, not the algorithm itself.