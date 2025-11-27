## 1. Introduction 🎯

### 1.1 What are PGP and GPG? 🔐

**PGP (Pretty Good Privacy)**: An encryption program developed by Phil Zimmermann in 1991. It established the standard for data security and digital signatures.

**GPG (GNU Privacy Guard)**: 🌟 An open-source PGP implementation! Follows the OpenPGP standard and is completely free.

### 1.2 Why Should We Use GPG? 💪
- ✅ **Privacy**: Encrypt your files and messages
- ✅ **Authentication**: Verify senders with digital signatures
- ✅ **Integrity**: Ensure data hasn't been modified
- ✅ **Free**: Completely open source and free!

### 1.3 Basic Concepts 🧠

| Concept | Description | Emoji |
|---------|-------------|--------|
| **Public Key** | Shared with everyone, used for encryption | 🔑 |
| **Private Key** | Stays only with you, used for decryption | 🗝️ |
| **Key Pair** | Public + Private key combination | 🔗 |
| **Key ID** | Unique identifier of the key | 🆔 |

---
## 2. Key Management 🔑

### 2.1 🆕 Creating New Key Pair

```bash
gpg --full-generate-key
```

**Step-by-step process:**
1. 📝 **Key Type**: `RSA and RSA` (Press Enter)
2. 🏗️ **Key Size**: `4096` (more secure!)
3. ⏰ **Validity Period**: `0` (unlimited) or your own duration
4. 👤 **User Information**:
   - Your real name
   - Email address
   - Description (optional) 📝
5. 🔒 **Set Passphrase**: Choose a strong passphrase!

### 2.2 📋 Listing Keys

```bash
# 🔓 List public keys
gpg --list-keys

# 🔐 List private keys
gpg --list-secret-keys

# 🔍 Detailed list
gpg --list-keys --keyid-format LONG
```

**Example output:**
```
pub   rsa4096 2023-01-01 [SC] [expires: 2028-01-01]
      ABCDEF1234567890ABCDEF1234567890ABCDEF12
uid           [ultimate] John Doe <john@example.com>
sub   rsa4096 2023-01-01 [E] [expires: 2028-01-01]
```

---
## 3. 📤📥 Key Export and Import

### 3.1 📤 Public Key Export

```bash
# 📄 ASCII format (readable)
gpg --armor --export john@example.com > john_public_key.asc

# 💾 Binary format
gpg --export john@example.com > john_public_key.gpg
```

### 3.2 📥 Public Key Import

```bash
# 📂 Import from file
gpg --import friend_public_key.asc

# 🌐 Import from keyserver
gpg --keyserver keyserver.ubuntu.com --recv-keys ABCDEF12
```

### 3.3 ⚠️ Private Key Backup (Be Careful!)

```bash
# 🔐 Backup private key (BE VERY CAREFUL!)
gpg --armor --export-secret-keys john@example.com > john_private_key_backup.asc
```

---
## 4. 🔒 File Encryption and Decryption

### 4.1 🔒 File Encryption

```bash
# 👤 Encrypt for specific recipient
gpg --encrypt --recipient friend@example.com secret_file.txt

# 💾 Specify output file
gpg --output encrypted_file.gpg --encrypt --recipient friend@example.com file.txt

# 📄 Encrypt in ASCII format
gpg --armor --encrypt --recipient friend@example.com file.txt
```

### 4.2 🔓 File Decryption

```bash
# 🤖 Automatic output (with original filename)
gpg --decrypt encrypted_file.gpg

# 🎯 Specify output file
gpg --output decrypted_file.txt --decrypt encrypted_file.gpg
```

### 4.3 🤝 Encrypting for Yourself

```bash
# 🔄 Encrypt with your own public key (for backup)
gpg --encrypt --recipient john@example.com backup_file.txt
```

---
## 5. ✍️ Signing and Verification

### 5.1 📝 File Signing

```bash
# 📎 Create separate signature file
gpg --detach-sign --armor file.txt
# → creates file.txt.sig

# 📦 Create signed file
gpg --sign file.txt
# → creates file.txt.gpg
```

### 5.2 ✅ Signature Verification

```bash
# 🔍 Verify signature
gpg --verify file.txt.sig file.txt

# 📦 Verify and decrypt signed file
gpg --decrypt file.txt.gpg
```

---
## 6. 🚀 Practical Examples

### Example 1: 🎯 First Key and Encryption

```bash
# 1. 🔑 Create key
gpg --full-generate-key

# 2. 📋 View my keys
gpg --list-keys

# 3. 📤 Share my public key
gpg --armor --export me@example.com > my_public_key.asc

# 4. 🔒 Encrypt note to myself
echo "This is a very secret note!" > secret_note.txt
gpg --encrypt --recipient me@example.com secret_note.txt

# 5. 🔓 Decrypt
gpg --decrypt secret_note.txt.gpg
```

### Example 2: 👥 Secure Communication with Friend

```bash
# 1. 📥 Import friend's public key
gpg --import alice_public_key.asc

# 2. 💌 Send encrypted message to friend
echo "Hello Alice, this is a secret message!" > message.txt
gpg --encrypt --recipient alice@example.com message.txt

# 3. 📩 Decrypt encrypted file from friend
gpg --decrypt alice_message.txt.gpg
```

### Example 3: 📎 Sending Signed Files

```bash
# 1. ✍️ Sign file
gpg --detach-sign --armor contract.pdf

# 2. 📤 Send signature and file
# → contract.pdf and contract.pdf.sig

# 3. ✅ Verification on recipient side
gpg --verify contract.pdf.sig contract.pdf
```

---
## 7. 🎨 Useful Tips

### 7.1 🌈 Colorful Output
```bash
# For colored output in terminal
gpg --list-keys --keyid-format 0xLONG
```

### 7.2 🔢 Key ID Usage
```bash
# Operations with short Key ID
gpg --encrypt --recipient ABCDEF12 file.txt

# With long Key ID (more secure)
gpg --encrypt --recipient ABCDEF1234567890 file.txt
```

### 7.3 🗂️ Multiple Recipients
```bash
# Encrypt for multiple recipients
gpg --encrypt --recipient john@example.com --recipient alice@example.com file.txt
```