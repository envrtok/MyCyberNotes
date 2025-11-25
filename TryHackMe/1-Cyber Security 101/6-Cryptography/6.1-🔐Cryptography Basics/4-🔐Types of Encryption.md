Encryption falls into **two main categories**:

1. **Symmetric (Private Key Cryptography)**
2. **Asymmetric (Public Key Cryptography)**

---

## 🟢 Symmetric Encryption

- **Same key** used for both encryption and decryption.
- Key secrecy is critical → challenge in securely sharing the key.
- Example scenario: password-protected document → password must be shared via secure channel.

### ✨ Examples

- **DES (1977)** → 56-bit key, broken in <24 hours by 1999.
- **3DES (Triple DES)** → 168-bit key (effective ~112 bits), deprecated in 2019.
- **AES (2001)** → modern standard, key sizes 128, 192, 256 bits.

👉 AES is the current standard; DES/3DES are legacy.

---

## 🔵 Asymmetric Encryption

- Uses **two keys**:
    - Public key → encrypt
    - Private key → decrypt
- Known as **public key cryptography**.
- Slower than symmetric, but solves the **key distribution problem**.

### ✨ Examples

- **RSA** → 2048-bit minimum, stronger with 3072/4096 bits.
- **Diffie-Hellman** → secure key exchange, min 2048-bit.
- **ECC (Elliptic Curve Cryptography)** → shorter keys with equivalent security (e.g., 256-bit ECC ≈ 3072-bit RSA).

👉 Based on **mathematical problems** that are easy one way but infeasible to reverse (e.g., factoring large primes, discrete logarithms).

---

## 📊 Quick Recap Table

|Type|Keys Used|Strengths|Weaknesses|Examples|
|---|---|---|---|---|
|Symmetric|Same key for encrypt/decrypt|Fast, efficient|Key distribution problem|DES, 3DES, AES|
|Asymmetric|Public key + Private key|Solves key sharing, strong security|Slower, larger keys|RSA, Diffie-Hellman, ECC|

---

## 🧩 New Terms

- **Alice & Bob** → fictional characters in cryptography examples.
- **Symmetric encryption** → one shared secret key.
- **Asymmetric encryption** → public key (shared) + private key (secret).

---

# 🎯 Takeaway

- **Symmetric** → efficient, but key distribution is hard.
- **Asymmetric** → slower, but solves distribution with public/private key pairs.
- Modern systems often use **hybrid encryption** → asymmetric for key exchange, symmetric for bulk data.