Problem:** Symmetric encryption requires a shared secret key, but securely transmitting that key is difficult.  
**Solution:** Diffie-Hellman allows two parties to establish a **shared secret** over an insecure channel without prior agreement.

---

## 🧩 Core Idea

- Two parties (Alice & Bob) agree on **public values**:
    - Large prime number **p**
    - Generator **g** (where 0 < g < p)
- Each party chooses a **private key** (a, b).
- They compute **public keys**:
    - Alice: A = g^a mod p
    - Bob: B = g^b mod p
- They exchange A and B.
- Each computes the **shared secret**:
    - Alice: B^a mod p
    - Bob: A^b mod p
- Both results equal g^(ab) mod p → identical shared secret.

---

## 📊 Numerical Example (Simplified)

- Public values: p = 29, g = 3
- Alice’s private key: a = 13 → A = 3^13 mod 29 = 19
- Bob’s private key: b = 15 → B = 3^15 mod 29 = 26
- Exchange: Alice sends 19, Bob sends 26
- Shared secret:
    - Alice: 26^13 mod 29 = 10
    - Bob: 19^15 mod 29 = 10
- Result: Shared secret = **10**

👉 In practice, p and g are **hundreds of digits long** for security.

![[Pasted image 20251126185533.png]]

---

## 🔐 Security Basis

- Relies on the **Discrete Logarithm Problem**:
    - Easy to compute g^a mod p.
    - Hard to reverse (find a given g^a mod p).
- Security grows with larger primes.

---

## 🌍 Real-World Use

- Often combined with **RSA**:
    - Diffie-Hellman → key agreement (shared secret).
    - RSA → authentication, digital signatures, key transport.
- Used in protocols like **TLS/SSL**, VPNs, and secure messaging.
- Prevents **man-in-the-middle attacks** when paired with authentication.

---

## 📊 Quick Recap Table

|Step|Alice|Bob|
|---|---|---|
|Private key|a = 13|b = 15|
|Public key|A = g^a mod p = 19|B = g^b mod p = 26|
|Exchange|Sends A|Sends B|
|Shared secret|B^a mod p = 10|A^b mod p = 10|

---

# 🎯 Takeaway

- Diffie-Hellman solves the **key distribution problem**.
- Shared secret → used for **symmetric encryption**.
- Combined with RSA → provides both **confidentiality** and **authenticity**.