**Cryptography** = practice and study of techniques for **secure communication** in the presence of adversaries.  
Its ultimate purpose → ensure **confidentiality, integrity, and authenticity** of data.

---

## 🎯 Core Goals

- **Confidentiality** → prevent unauthorized disclosure of data
- **Integrity** → prevent unauthorized modification of data
- **Authenticity** → verify sender/receiver identity

---

## 📡 Everyday Uses

- **Login credentials** → encrypted in transit (e.g., TryHackMe login)
- **SSH sessions** → encrypted tunnel prevents eavesdropping
- **Online banking** → certificates verify server authenticity
- **File downloads** → hash functions confirm file integrity

---

## 🏢 Compliance & Standards

- **PCI DSS** → required for handling credit card data
    - Encrypt data **at rest** and **in motion**
- **Medical records** → governed by country-specific laws:
    - 🇺🇸 **HIPAA / HITECH**
    - 🇪🇺 **GDPR**
    - 🇬🇧 **DPA**
- These frameworks enforce **cryptographic protection** for sensitive data.

---

## 📊 Quick Recap Table

|🔑 Goal|📌 Example|
|---|---|
|Confidentiality|Encrypted login credentials|
|Integrity|File hash verification|
|Authenticity|SSL/TLS certificates|
|Compliance|PCI DSS, HIPAA, GDPR|

---

# 🎯 Takeaway

Cryptography is **everywhere in the digital world** — often invisible to users.  
It underpins secure communication, protects sensitive data, and ensures compliance with global standards.