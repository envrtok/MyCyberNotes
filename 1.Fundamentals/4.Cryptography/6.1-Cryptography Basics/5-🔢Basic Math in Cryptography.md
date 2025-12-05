Modern cryptography relies heavily on **mathematical operations**. Two fundamental ones are:

1. **XOR (Exclusive OR)**
2. **Modulo (Remainder)**

---

## 🟢 XOR Operation (⊕)

- **Definition** → compares two bits:
    - Same → 0
    - Different → 1

### Truth Table

|A|B|A ⊕ B|
|---|---|---|
|0|0|0|
|0|1|1|
|1|0|1|
|1|1|0|

### Example

```
1010 ⊕ 1100 = 0110
```

### Properties

- **A ⊕ A = 0**
- **A ⊕ 0 = A**
- **Commutative** → A ⊕ B = B ⊕ A
- **Associative** → (A ⊕ B) ⊕ C = A ⊕ (B ⊕ C)

### Cryptography Use

- Simple symmetric encryption:
    - Ciphertext: **C = P ⊕ K**
    - Decryption: **C ⊕ K = P**
- ⚠️ In practice → requires key as long as plaintext (basis of one-time pad).

---

## 🔵 Modulo Operation (% or mod)

- **Definition** → remainder after division.
- Example:
    - 25 % 5 = 0 → 25 = 5 × 5 + 0
    - 23 % 6 = 5 → 23 = 3 × 6 + 5
    - 23 % 7 = 2 → 23 = 3 × 7 + 2

### Properties

- Always returns **0 ≤ result < divisor**.
- **Not reversible** → many values satisfy same remainder.
    - Example: x % 5 = 4 → infinite possible x values.

### Cryptography Use

- Essential in **modular arithmetic** → basis for RSA, Diffie-Hellman, ECC.
- Provides finite ranges → keeps numbers manageable even when very large.

---

## 📊 Quick Recap Table

|Operation|Symbol|Key Property|Cryptography Use|
|---|---|---|---|
|XOR|⊕ or ^|A ⊕ A = 0, reversible with same key|Symmetric encryption, one-time pad|
|Modulo|% or mod|Result in [0, n−1], not reversible|Modular arithmetic in RSA, DH, ECC|

---

# 🎯 Takeaway

- **XOR** → lightweight, reversible, forms the basis of symmetric encryption.
- **Modulo** → keeps large numbers bounded, critical for public-key cryptography.