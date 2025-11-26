RSA is a **public-key encryption algorithm** used for secure communication over insecure channels.  
Its security relies on the **difficulty of factoring large numbers**.

---

## 🧩 The Math Behind RSA

- **Easy** → multiply two large primes.
- **Hard** → factor their product back into primes.
- Example:
    - 113 × 127 = 14351 (easy)
    - Factoring 14351 back into primes (harder).
- Real-world RSA uses primes with **hundreds of digits** → factoring becomes **computationally infeasible**.

---

## 🔄 RSA Algorithm (Simplified Example)

1. **Key Generation**
    
    - Choose primes: p = 157, q = 199
    - Compute n = p × q = 31243
    - Compute ϕ(n) = (p−1)(q−1) = 30888
    - Choose e = 163 (coprime with ϕ(n))
    - Compute d = 379 (satisfies e × d ≡ 1 mod ϕ(n))
    - Public key = (n, e) = (31243, 163)
    - Private key = (n, d) = (31243, 379)
2. **Encryption**
    
    - Plaintext x = 13
    - Ciphertext y = xe mod n = 13163 mod 31243 = 16341
3. **Decryption**
    
    - x = yd mod n = 16341379 mod 31243 = 13
    - Original plaintext recovered.

👉 In practice, primes are **hundreds of digits long** → secure against brute force.

---

## 📊 RSA Variables (CTF Context)

|Variable|Meaning|
|---|---|
|p, q|Large prime numbers|
|n|Product of p × q|
|e|Public exponent|
|d|Private exponent|
|m|Plaintext message|
|c|Ciphertext|

---

## 🎯 RSA in CTFs

- Common challenge: given some of **p, q, n, e, d, c**, recover plaintext.
- Tools:
    - **RsaCtfTool** → automates attacks and decryption.
    - **rsatool** → helps compute missing RSA parameters.
- Typical tasks: factor n, compute d, decrypt c.

---

# 🎯 Takeaway

- RSA = secure because factoring **n = p × q** is hard.
- Public key (n, e) → encrypt.
- Private key (n, d) → decrypt.
- Widely used in secure protocols (TLS, HTTPS, email encryption).
- In CTFs → knowing RSA math and variables is essential to break challenges.