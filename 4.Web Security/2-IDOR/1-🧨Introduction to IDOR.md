### 🔍 What is IDOR?

- IDOR (**Insecure Direct Object Reference**) occurs when an application exposes internal object references (like user IDs, invoice numbers, file names) **without proper authorization checks**.
- If a user can manipulate these references to access data they shouldn't — that's an IDOR vulnerability.

### 🧪 Example

```http
GET /user/123
```

- If changing `123` to `124` lets you view another user's profile **without being authorized**, the app is vulnerable to IDOR.

### ⚠️ Common Misconceptions

- **Encoding or obfuscating IDs (e.g., base64, UUID)** does **not** prevent IDOR.
    - Example: `GET /user/MTIz` → still guessable, still vulnerable if authorization is missing.

---

## 🧠 Core Concepts Behind IDOR

|Concept|Definition|Abuse Type|
|---|---|---|
|**Authentication**|Verifying who you are|**Vertical privilege escalation** — impersonating higher-privileged users|
|**Authorization**|Verifying what you're allowed to access|**Horizontal privilege escalation** — accessing peer-level data (IDOR)|

- IDOR is a **horizontal privilege escalation** vector:  
    You stay as yourself, but access someone else's data.