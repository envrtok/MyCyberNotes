**SSH (Secure Shell)** is a protocol that allows you to **connect to and control remote machines securely** over an unsecured network.

It provides:

- **Confidentiality** – data is encrypted 🔒
    
- **Integrity** – data cannot be altered unnoticed ✅
    
- **Authentication** – verifies identity 🪪
    

---

## 💻 Basic Usage

```bash
ssh <username>@<ip-address>
```

```bash
# When prompted:
password: <your-password>
```

---

## ⚙️ How It Works

### 🛫 Step 0: Starting

When you type

```bash
ssh username@ip-address
```

your client parses the **username**, **host**, and **port** information, then opens a **TCP socket** to the SSH port (default **22**).

---

### 🔄 Step 1: Version Exchange

The **client** sends its SSH version, and the **server** replies with its own.  
Both confirm they’re speaking the same protocol version (**SSH-2.0**).

---

### 🧮 Step 2: Algorithm Negotiation

The client proposes a list of supported algorithms.  
The server picks the best match and replies with its choice.

They agree on:

- Key exchange method 🔑
    
- Host key type 🧾
    
- Encryption algorithm 🧠
    
- MAC (Message Authentication Code) ✅
    
- Optional compression 🗜️
    

---

### 🤝 Step 3: Key Exchange (Diffie–Hellman)

A **shared secret session key** is created using the **Diffie–Hellman algorithm**, ensuring no eavesdropper can know it.

**How it works:**

1. Client chooses random `a`, computes `A = g^a mod p`, sends `A`.
    
2. Server chooses random `b`, computes `B = g^b mod p`, sends `B`.
    
3. Both compute:
    
    - Client: `K = B^a mod p`
        
    - Server: `K = A^b mod p`
        

They both get the **same secret key `K`**, which no one else can derive 🔥

---

#### 🔑 Key Derivation

SSH **doesn’t use `K` directly** for encryption or authentication.  
Instead, it **derives several independent session keys** from it — one for each purpose and direction.

From the shared secret `K`, SSH generates:

- `client_to_server_encryption_key` 🔒
    
- `server_to_client_encryption_key` 🔒
    
- `client_to_server_MAC_key` ✅
    
- `server_to_client_MAC_key` ✅
    

This ensures:

- Each direction (upload/download) uses **different keys**
    
- Encryption and MAC keys are **separate**
    
- The original secret `K` is **never reused directly**
    

> 💡 In short: Diffie–Hellman creates the root secret, and SSH expands it into multiple secure working keys for the session.

---

### 🧍 Step 4: Authentication

The **server verifies your identity** — either:

- via **password**, or
    
- using your **SSH key pair** (public/private).
    

Authentication happens **on the client side**, confirming that _you_ are who you claim to be.

---

### 🎬 Step 5: Session Establishment

Once authentication succeeds, a **secure session** is established between client and server.

---

### 📡 Step 6: Data Transfer & Command Execution

All data (commands, responses, files, etc.) are:

- **Encrypted** with the session encryption key 🔐
    
- **Authenticated** with a **MAC** derived from its own MAC key ✅
    

This provides both **confidentiality** and **integrity** for every packet.

---

#### 🔒 How Encryption and MAC Work Together

When you send data:

1. The SSH client **encrypts** your plaintext using the encryption key.
    
2. It then **computes a MAC** (Message Authentication Code) using the MAC key and appends it.
    
3. The packet is sent securely through the SSH tunnel.
    

When the server receives it:

1. It **verifies the MAC** to ensure the packet wasn’t modified.
    
2. If valid, it **decrypts** the data using the same session key.
    

If the MAC check fails, the packet is rejected — preventing tampering or injection attacks.

---

### 🧭 Data Flow Diagram

```
   ┌──────────────────────────────────────────────┐
   │                CLIENT SIDE                   │
   └──────────────────────────────────────────────┘
           │
           ▼
   [Plaintext Data]
           │
           ▼
   Encrypt with Encryption Key 🔒
           │
           ▼
   Add MAC (Message Authentication Code) ✅
           │
           ▼
     ───── SEND OVER NETWORK ─────▶
           │
           ▼
   ┌──────────────────────────────────────────────┐
   │                SERVER SIDE                   │
   └──────────────────────────────────────────────┘
           │
           ▼
   Verify MAC ✅ → (if OK) → Decrypt 🔓
           │
           ▼
      [Plaintext Restored]
```

> 🧠 **Summary:**  
> SSH uses **keys derived from the Diffie–Hellman secret** for both **encryption** (privacy) and **MAC** (integrity).  
> Every byte you send is encrypted and verified before being read.

---

## 🧠 Security Summary

In short, **SSH builds a secure tunnel** between your computer (client) and the remote host (server):

| Protection               | Mechanism                   | Purpose                                    |
| ------------------------ | --------------------------- | ------------------------------------------ |
| 🔑 **Shared Secret Key** | Diffie–Hellman              | Root secret for session                    |
| 🧩 **Key Derivation**    | Derived from DH secret      | Creates separate keys for encryption & MAC |
| 🔐 **Encryption**        | Symmetric cipher            | Keeps data private                         |
| ✅ **MAC**                | Message Authentication Code | Detects tampering                          |
| 🧍**Authentication**     | Password / Key              | Confirms user identity                     |

---
