# 🔒 Obfuscation in Action

### 🎯 What is Obfuscation?

- **Obfuscation** = making code **hard to read** for humans but still **executable** by browsers.
- Often used to **hide logic**, **compress/minify files**, or **protect intellectual property**.
- Can also be abused by attackers to conceal **malicious payloads**.

---

## 🛠️ Minifying & Obfuscating

1. Copy the contents of `hello.js`.
2. Paste into an **online JS obfuscator**.
3. Tool outputs **gibberish-like code** (variables renamed, logic scrambled).
4. Browser still executes it correctly.

👉 Example:  
Original (readable):

```javascript
function hi() {
  alert("Welcome to THM");
}
hi();
```

Obfuscated (unreadable but functional):

```javascript
(function(_0x114713,_0x2246f2){...})(...);
function hi(){...alert("Welcome to THM");}
hi();
```

---

## 🔍 Observing in Chrome

- Replace `hello.js` with obfuscated code.
- Reload `hello.html`.
- Inspect under **Sources tab** → code looks scrambled but works the same.

---

# 🔓 Deobfuscation

### 🎯 What is Deobfuscation?

- Process of **reversing obfuscation** to make code **human-readable again**.
- Useful for **security analysis**, **debugging**, or **learning original logic**.

---

## 🛠️ Steps

1. Copy obfuscated JS.
2. Paste into an **online deobfuscator**.
3. Tool outputs **clean, readable JS**.

👉 Example:  
Obfuscated:

```javascript
(function(_0x114713,_0x2246f2){...})(...);
```

Deobfuscated:

```javascript
function hi() {
  alert("Welcome to THM");
}
hi();
```

---

# ✅ Key Takeaways

- Obfuscation hides code from humans, not from browsers.
- Attackers use it to **conceal malicious scripts**.
- Deobfuscation tools can **restore readability** quickly.
- Always inspect obfuscated code before trusting it.

---

📊 **Quick Comparison Table**

|Process|Purpose|Output Style|Risk/Use Case|
|---|---|---|---|
|**Minify**|Reduce file size|Shortened, compact|Faster load times|
|**Obfuscate**|Hide logic, protect code|Gibberish-like|Can conceal malware|
|**Deobfuscate**|Restore readability|Human-readable|Security analysis, debugging|
