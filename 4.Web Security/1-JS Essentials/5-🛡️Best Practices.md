### 🎯 Goal

Reduce attack surface and minimize exploitation risks when developing web applications with JavaScript.

---

## 🚫 Avoid Relying on Client-Side Validation Only

- Client-side validation (e.g., form checks) can be **disabled or manipulated** by attackers.
- Always enforce **server-side validation** to ensure data integrity.

---

## 📦 Refrain from Adding Untrusted Libraries

- JS allows inclusion of external scripts via `<script src="...">`.
- Attackers upload **malicious libraries** with names resembling legitimate ones.
- ✅ Only use **trusted, verified sources** (official CDNs, signed packages).

---

## 🔑 Avoid Hardcoded Secrets

- Never embed **API keys, tokens, or credentials** directly in JS.
- Users can easily view source code (`CTRL+U`) and extract secrets.

❌ Bad Practice:

```javascript
const privateAPIKey = 'pk_TryHackMe-1337';
```

✅ Better Practice:

- Store secrets on the **server side**.
- Use **environment variables** or secure vaults.

---

## ⚡ Minify & Obfuscate Your Code

- **Minify** → reduces file size, improves load time.
- **Obfuscate** → makes code harder to reverse engineer.
- ✅ Always apply these steps in **production**.
- Note: Attackers can still deobfuscate, but it adds **friction and effort**.

---

# 📊 Quick Reference Table

|Practice|Why It Matters|Secure Approach|
|---|---|---|
|Client-side validation only|Can be bypassed|Add server-side validation|
|Untrusted libraries|Risk of malicious code injection|Use trusted CDNs/repos|
|Hardcoded secrets|Easily exposed in source code|Store on server/env vars|
|No minify/obfuscation|Easier for attackers to read logic|Minify + obfuscate in prod|
