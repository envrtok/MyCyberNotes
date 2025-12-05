### 🛡️ Vulnerability

- **Definition:** A **weakness or flaw** in software, hardware, or configuration that can be exploited.
- **Purpose:** It’s the **reason exploits exist**—without vulnerabilities, there’s nothing to attack.
- **Examples:**
    - Unpatched SMB service (MS17-010)
    - Misconfigured web server allowing directory traversal
    - Buffer overflow in a legacy application
- **Analogy:** The **broken lock** that makes the door exploitable.

---

### ⚡ Exploit

- **Definition:** Code or technique that takes advantage of a **vulnerability** in a target system.
- **Purpose:** Provides the _entry point_ by breaking into the system.
- **Examples:**
    - EternalBlue SMB exploit
    - SQL injection exploit
    - Buffer overflow exploit
- **Analogy:** The **lockpick** that opens the door.

---

### 📦 Payload

- **Definition:** Code that runs **after the exploit succeeds**.
- **Purpose:** Defines _what happens next_ once access is gained.
- **Types:**
    - Reverse shell
    - Bind shell
    - Meterpreter session
    - Command execution
- **Analogy:** The **tools you carry inside** once the door is open.