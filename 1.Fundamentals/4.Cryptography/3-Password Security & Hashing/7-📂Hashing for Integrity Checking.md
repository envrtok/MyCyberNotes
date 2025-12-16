We’ve already explored how hashing secures passwords in authentication systems. Now let’s look at its second major use: **data integrity**.

---

## 🔍 Integrity Checking

- **Property of hashing**:
    - Same input → always same output.
    - Even a **single bit change** → drastically different hash.
- **Use case**:
    - Verify files haven’t been modified.
    - Confirm downloads are identical to the official source.

### Example: Fedora ISO Verification

A checksum file lists official SHA256 hashes:

```
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

# Fedora-Workstation-Live-osb-40-1.14.x86_64.iso: 2623733760 bytes
SHA256 (Fedora-Workstation-Live-osb-40-1.14.x86_64.iso) = 8d3cb4d99f27eb932064915bc9ad34a7529d5d073a390896152a8a899518573f

# Fedora-Workstation-Live-x86_64-40-1.14.iso: 2295853056 bytes
SHA256 (Fedora-Workstation-Live-x86_64-40-1.14.iso) = dd1faca950d1a8c3d169adf2df4c3644ebb62f8aac04c401f2393e521395d613
```

👉 If your `sha256sum` output matches the listed hash, your file is authentic and unchanged.

---

## 📑 Other Uses of Hashing

- **Duplicate detection**:
    - If two files have the same hash → they are identical.
    - Useful for cleaning up duplicate documents.

---

## 🔐 HMACs (Keyed-Hash Message Authentication Codes)

An **HMAC** combines a **hash function** with a **secret key** to provide:

- **Authenticity** → proves the sender is genuine.
- **Integrity** → proves the message hasn’t been altered.

### How HMAC Works (Step-by-Step)

1. Pad the secret key to the block size of the hash function.
2. XOR the padded key with a constant (`ipad`).
3. Hash the message using the hash function with this XORed key.
4. XOR the padded key with another constant (`opad`).
5. Hash the result from step 3 with this new key.
6. Output = **HMAC value** (fixed-size string).

### Formula

_HMAC(K,M) = H((K⊕ opad)||((K⊕ ipad)||M))_

- (K) = secret key
- (M) = message
- (H) = hash function
- (⊕) = XOR
- `ipad` / `opad` = constants used for inner/outer hashing

---

## 🧩 Key Takeaways

- Hashing ensures **file integrity** by detecting even tiny changes.
- Checksums (like SHA256) are widely used to verify downloads.
- HMACs extend hashing with a **secret key**, ensuring both **authenticity** and **integrity**.