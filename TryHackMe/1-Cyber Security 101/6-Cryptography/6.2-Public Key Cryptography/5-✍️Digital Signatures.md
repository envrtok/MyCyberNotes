## 📌 Analogue vs Digital

- **Analogue world** → handwritten signatures confirm identity, authorisation, or agreement.
- **Digital world** → requires **digital signatures** to prove authenticity and integrity of electronic data.

---

## 🔑 What is a Digital Signature?

- **Purpose** → verify authenticity (who signed) + integrity (unchanged content).
- **Mechanism** → asymmetric cryptography:
    - Sign with **private key**.
    - Verify with **public key**.
- **Legal value** → in many countries, digital signatures = physical signatures.

### Simplest Form

- Encrypt document/hash with private key.
- Recipient decrypts with public key → compare with original hash.
- Confirms integrity + authenticity.

⚠️ **Electronic signatures** (e.g., pasted images) ≠ digital signatures → no integrity guarantee.

---

# 📜 Certificates

## 📌 Purpose

- Certificates prove **identity** of servers, users, or organisations.
- Common use → **HTTPS websites**.

## 🔗 Chain of Trust

- Certificates are signed by trusted **Certificate Authorities (CAs)**.
- Browser/OS trusts root CAs → trust flows down the chain.
- Example:
    - Website certificate → signed by organisation.
    - Organisation → trusted by CA.
    - CA → trusted by browser.
- Result → browser trusts the website’s certificate.

---

## 🌍 Real-World Example

- To enable HTTPS → need a **TLS certificate**.
- Options:
    - Paid certificates from CAs (annual fee).
    - Free certificates from **Let’s Encrypt**.
- Modern websites → expected to use HTTPS for security.

---

## 📊 Quick Recap Table

|Concept|Explanation|
|---|---|
|Digital Signature|Private key signs, public key verifies|
|Integrity Check|Compare decrypted hash with file hash|
|Electronic vs Digital|Image ≠ cryptographic proof|
|Certificates|Prove identity via chain of trust|
|Root CAs|Trusted by OS/browser, anchor trust|
|TLS Certificates|Required for HTTPS, can be free (Let’s Encrypt)|

---

# 🎯 Takeaway

- **Digital signatures** → guarantee authenticity + integrity.
- **Certificates** → prove identity via trusted CAs.
- Together, they underpin secure communication protocols like **HTTPS/TLS**.