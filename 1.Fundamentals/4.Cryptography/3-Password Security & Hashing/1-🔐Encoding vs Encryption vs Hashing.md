# 🔤 Encoding

- 📡 Transforms data for usability for different systems.
- 🚫 No key usage.
- 🔁 It can reversible with using format.
- 🧮 **Algorithms**: Base64, ASCII, Unicode, URL Encoding, Hex ...
- 🌍 **General Usage**: Email Attachments, Web URLs, Displaying Text, API Data ...
- ✉️ **Analogy:** Writing a message in Morse Code. It looks secret to someone who doesn't know it, but anyone with a cheat sheet can read it perfectly.

---

# 🔒 Encryption

- 🔐 Encryption transforms data to keep it secret.
- 🔑 Uses keys. (private keys, public keys, session keys)
- 🔁 It can reversible with key.
- 🧮 **Algorithms**: AES, RSA, PGP ...
- 🌍 **General Usage**: Secure Messaging, HTTPS, SSH, VPNs ...
- 📦 **Analogy:** Putting a letter inside a safe and mailing the safe. Only the person with the combination (the key) can open it and read the letter.

---

# 🧩 Hashing

- ➡️ One-way function. One data only has one hash.
- 📏 Gives information about data's integrity.
- 🚫 Impossible to reverse. Hashing gives one result. But in the reverse direction (Hash ➡️ Input), there are **infinite** possible results.
- 🧮 **Algorithms**: SHA-256, MD5, Bcrypt ...
- 🌍 **General Usage**: Password Storage, File Integrity, Blockchain/Crypto, Digital Signitures ...

---

## 🌍 Real World Example

- 🔒 **Encryption:** The user sends their password over the internet. The connection is **Encrypted** (HTTPS) so hackers on the WiFi can't intercept it.
    
- 🧩 **Hashing:** The server receives the password. It does _not_ save the actual password in the database. Instead, it **Hashes** the password and saves the hash. Next time the user logs in, the system hashes the input and compares it to the stored hash.
    
- 🔤 **Encoding:** The server sends a session token back to the user to keep them logged in. This token might be a JSON object **Encoded** in Base64 so it can be safely stored in a browser cookie.