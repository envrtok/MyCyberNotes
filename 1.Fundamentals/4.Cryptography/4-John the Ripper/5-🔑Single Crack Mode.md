So far, we’ve used **wordlist mode** in John the Ripper to brute-force hashes. But John also has another approach: **Single Crack Mode**.

In this mode, John uses information from the **username** (and related fields) to heuristically guess possible passwords by applying transformations known as **word mangling**.

---

## 🌀 Word Mangling

Word mangling means taking a base word (like a username) and applying rules to generate variations.

**Example: username = `Markus`**

Possible password guesses:

- `Markus1`, `Markus2`, `Markus3`
- `MArkus`, `MARkus`, `MARKus`
- `Markus!`, `Markus$`, `Markus*`

👉 John builds a custom dictionary using **mangling rules** that mutate the original word. This exploits weak password practices where users base passwords on their usernames or related info.

---

## 📇 GECOS Field

John also leverages the **GECOS field** in UNIX/Linux systems:

- Found in `/etc/passwd` (5th field, separated by `:`).
- Stores general user info: full name, office number, phone number, etc.
- John can use this data (e.g., full name, home directory) to expand its mangled wordlist when cracking `/etc/shadow` hashes.

This makes Single Crack Mode more powerful, as it uses **contextual user information**.

---

## ⚙️ Using Single Crack Mode

**Syntax:**

```
john --single --format=[format] [path to file]
```

- `--single` → Enables Single Crack Mode
- `--format=[format]` → Specifies the hash type (e.g., `raw-sha256`)
- `[path to file]` → File containing the hashes

**Example:**

```
john --single --format=raw-sha256 hashes.txt
```

---

## 📂 File Format Requirement

For Single Crack Mode, John needs the hash file to include the **username** before the hash:

- ❌ Incorrect:
    
    ```
    1efee03cdcb96d90ad48ccc7b8666033
    ```
    
- ✅ Correct:
    
    ```
    mike:1efee03cdcb96d90ad48ccc7b8666033
    ```
    

This way, John knows which username to base its mangling rules on.

---

## 🔑 Workflow Summary

1. Prepare hash file → prepend username to each hash.
2. Run John with `--single` mode.
3. John generates mangled variations based on username + GECOS info.
4. Cracking proceeds using this custom wordlist.