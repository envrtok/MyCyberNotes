SSH (Secure Shell) provides secure remote login and communication.  
It relies on **public-key cryptography** for authenticating both the server and the client.

---

## 🖥️ Authenticating the Server

- When connecting, the client checks the server’s **public key fingerprint**.
- Example:
    
    ```
    The authenticity of host '10.10.244.173' can't be established.
    ED25519 key fingerprint is SHA256:...
    ```
    
- If unknown, the client prompts for confirmation.
- Accepting → fingerprint stored in `~/.ssh/known_hosts`.
- Future connections → silent unless the server’s key changes.
- Purpose → prevent **man-in-the-middle attacks**.

---

## 👤 Authenticating the Client

- **Password-based login** → common but less secure.
- **Key-based login** → preferred, uses public/private key pairs.
- Keys generated with `ssh-keygen`:
    - Algorithms: `rsa`, `dsa`, `ecdsa`, `ecdsa-sk`, `ed25519`, `ed25519-sk`.
    - Example:
        
        ```bash
        ssh-keygen -t ed25519
        ```
        
- Public key → copied to server (`authorized_keys`).
- Private key → stays on client, must remain secret.

---

## 🔐 SSH Key Algorithms

- **RSA** → widely used, longer keys (2048–4096 bits).
- **DSA** → legacy, designed for signatures.
- **ECDSA** → elliptic curve variant, smaller keys with equivalent security.
- **Ed25519** → modern, secure, efficient (Curve25519).
- **SK variants** → hardware-backed (e.g., YubiKey).

---

## ⚠️ SSH Private Keys

- Treat like **passwords** → never share.
- Passphrase protects private key locally (not sent to server).
- Tools like **John the Ripper** can brute-force weak passphrases.
- Permissions must be strict:
    
    ```bash
    chmod 600 ~/.ssh/id_ed25519
    ```
    

---

## 📂 Keys Trusted by Remote Host

- Stored in `~/.ssh/authorized_keys`.
- Only listed public keys can authenticate.
- Root access → should only allow key authentication (no passwords).

---

## 🛠️ Practical Use in Security

- **ssh -i privateKeyFile user@host** → specify private key file.
- **ssh-copy-id user@host** → copy public key to server.
- In **CTFs / pentesting**:
    - Uploading your public key to `authorized_keys` → stable shell access.
    - Useful for upgrading reverse shells → tab completion, Control-C handling, persistence.

---

## 📊 Quick Recap Table

|Concept|Explanation|
|---|---|
|Server Auth|Verify server’s public key fingerprint|
|Client Auth|Password or key-based (preferred)|
|Key Algorithms|RSA, DSA, ECDSA, Ed25519 (+ SK variants)|
|Private Key Rules|Never share, protect with passphrase, strict permissions|
|authorized_keys|File storing trusted public keys on server|
|Security Use|Stable shell, backdoor in CTFs/pentests|

---

# 🎯 Takeaway

SSH security depends on **mutual authentication**:

- Server proves identity with its public key.
- Client proves identity with its private key.
- Keys must be protected, permissions enforced, and passphrases strong.