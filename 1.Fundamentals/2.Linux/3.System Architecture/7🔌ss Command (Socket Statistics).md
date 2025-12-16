- 🎯 **Purpose:** Display detailed information about sockets (TCP, UDP, UNIX, etc.).
- 🛠️ **Use case:** Faster, more modern replacement for `netstat`.

---

## 📋 Basic Usage

```bash
ss
```

👉 Shows a summary of open non‑listening sockets.

---

## 🔑 Common Options

|Option|Meaning|Example|
|---|---|---|
|`-t`|Show TCP sockets|`ss -t`|
|`-u`|Show UDP sockets|`ss -u`|
|`-l`|Show listening sockets|`ss -l`|
|`-a`|Show all sockets (listening + non‑listening)|`ss -a`|
|`-n`|Show numeric addresses (skip DNS)|`ss -n`|
|`-p`|Show process using the socket|`ss -p`|
|`-r`|Resolve service names|`ss -r`|
|`-s`|Summary statistics|`ss -s`|
|`-4`|Show IPv4 sockets|`ss -4`|
|`-6`|Show IPv6 sockets|`ss -6`|

---

## 🧪 Practical Examples

- Show all listening TCP ports:

```bash
ss -tln
```

- Show UDP sockets with process info:

```bash
ss -ulpn
```

- Show all sockets with process names:

```bash
ss -ap
```

- Show summary statistics (like connections per protocol):

```bash
ss -s
```

- Show established connections only:

```bash
ss -t state established
```

---

## ⚡ Pro Tips

- Combine flags for precision:

```bash
ss -tulpn
```

👉 Shows TCP + UDP, listening, with process IDs.

- Use `state` filter for connection states:
    - `established` → active connections
    - `listen` → listening sockets
    - `closed` → closed connections