- ⚠️ Securing passwords strongly is very important thing.
- ❌ Most common mistakes are storing in plaintext, using encryption or weak hashing algorithm.
- 🔑 Encrypting doesn't been choosen because if someone gets key, they can crack password.
- 🛡️ But hashses are unreversable and anyone couldnt crack it.

---

## 📄 Storing in Plaintext

- 🚫 Storing passwords without hashing is obviously dangerous.
- 📂 rockyou is the most common password plaintext. It contains over 14 million passwords.
- 📍 `/usr/share/wordlists/rockyou.txt`
- 📊 `wc -l rockyou.txt` gives line number.
- 👀 `head -n 20 rockyou.txt` gives first 20 lines (passwords).

---

## 🌈 Rainbow Tables

- 📚 Rainbow tables contains hashes and their decrypted versions. An example below here:

|🔑 Hash|🔓 Password|
|---|---|
|02c75fb22c75b23dc963c7eb91a062cc|zxcvbnm|
|b0baee9d279d34fa1dfd71aadb908c3f|11111|
|c44a471bd78cc6c2fea32b9fe028d30a|asdfghjkl|
|d0199f51d2728db6011945145a1b607a|basketball|

- 🌐 Websites like crackstation.net and hashes.com contains massive rainbow tables with cracked passwords.
- 🧂 For protecting against rainbow tables, we add a salt to passwords.

---

## 🧂 Adding Salt to Passwords

### 🧩 The Logic of Salt

- **Salt = random extra data.**
- The system adds this random data next to your password, then hashes them together.
- 🔀 This way, even if two people use the same password, their stored results are different.

---

### 🔐 Why Does This Make It Safer?

- **Hash alone**:
    
    - `SHA256("123456")` → always the same result for everyone.
    - Hackers can use precomputed tables (rainbow tables) to crack it quickly.
- **Hash + Salt**:
    
    - 👤 User A: `SHA256("123456" + "abcXYZ")`
    - 👤 User B: `SHA256("123456" + "Q9!lm")`
    - Both typed the same password, but the outputs are completely different.
    - ⏳ Hackers must attack each salted hash separately, which is far more expensive and time‑consuming.

---

### 📌 Important Point

- You don’t type the salt when you log in.
- 🛠️ The system automatically generates and stores a unique salt for your account.
- 🔑 When you log in, the system takes your password, adds the stored salt, hashes it, and checks if it matches the saved hash.
- 🛡️ So salt is a **backend security layer** that works invisibly for you.

---

### 🎯 In Short

Salt makes passwords **unique and unpredictable**.  
Even if millions of people use the same password, each stored hash will be different, which makes large‑scale attacks much harder.
