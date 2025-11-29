## 📌 What Are Custom Rules?

Custom rules let you define your own **word mangling patterns**. Instead of relying only on John’s built-in rules, you can create rules that dynamically generate passwords based on what you know about the target’s password structure.

This is especially useful when:

- You know the organization enforces password complexity.
- You suspect predictable patterns (e.g., capital letter at the start, number + symbol at the end).

---

## 🔐 Common Custom Rules

Many organizations enforce complexity requirements:

- Lowercase letter
- Uppercase letter
- Number
- Symbol

Users often follow predictable patterns, such as:

```
Polopassword1!
```

Pattern breakdown:

- Capital letter at the start (`P`)
- Word (`olopassword`)
- Number (`1`)
- Symbol (`!`)

👉 Attackers exploit this predictability by defining rules that generate such variations automatically.

---

## ⚙️ Creating Custom Rules

Custom rules are defined in **`john.conf`**:

- On TryHackMe Attackbox: `/opt/john/john.conf`
- On most Linux installs: `/etc/john/john.conf`

### Rule Syntax

Rules are defined in sections like:

```
[List.Rules:RuleName]
```

**Common modifiers:**

- `Az` → Append characters to the end
- `A0` → Prepend characters to the start
- `c` → Capitalize characters positionally

**Character sets (inside `[]`):**

- `[0-9]` → Numbers 0–9
- `[A-Z]` → Uppercase letters
- `[a-z]` → Lowercase letters
- `[!£$%@]` → Symbols

---

## 🧩 Example Rule

Target password pattern: `Polopassword1!`

Rule definition:

```
[List.Rules:PoloPassword]
cAz"[0-9] [!£$%@]"
```

Explanation:

- `c` → Capitalize the first letter
- `Az` → Append characters at the end
- `[0-9]` → Add a number (0–9)
- `[!£$%@]` → Add one of these symbols

---

## ▶️ Using Custom Rules

Run John with your custom rule:

```
john --wordlist=[path to wordlist] --rule=PoloPassword [path to file]
```

- `--wordlist=` → Base wordlist
- `--rule=PoloPassword` → Apply your custom rule
- `[path to file]` → File containing the hashes

---

## 📝 Tips

- Speak the pattern out loud when writing rules (like regex).
- Jumbo John already includes many predefined rules (check around line 678 in `john.conf`).
- If your syntax fails, compare with existing examples.