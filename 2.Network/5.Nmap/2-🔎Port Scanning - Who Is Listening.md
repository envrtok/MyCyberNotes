After discovering **live hosts** with `-sn`, the next step is to identify **network services** listening on TCP/UDP ports.  
Common examples:

- 🌐 Web servers → TCP 80, 443
- 📡 DNS servers → UDP/TCP 53

---

## ⚡ TCP Port Scanning

### 1️⃣ Connect Scan (`-sT`)

- Completes full **TCP three-way handshake**.
- If port is open → connection established, then torn down with RST.
- If port is closed → target responds with RST-ACK.
- ✅ Reliable but **noisy** (logged easily).
- Example:
    
    ```bash
    nmap -sT 192.168.124.148
    ```
    

---

### 2️⃣ SYN Scan (Stealth) (`-sS`)

- Sends only **SYN packet** (first step of handshake).
- Open port → replies with SYN-ACK, Nmap responds with RST (no full connection).
- Closed port → replies with RST-ACK.
- ✅ Stealthier, fewer logs.
- Example:
    
    ```bash
    nmap -sS 192.168.124.148
    ```
    

---

## 📡 UDP Port Scanning (`-sU`)

- No handshake → sends UDP packets directly.
- Closed port → ICMP “port unreachable” response.
- Open port → may respond with service-specific data.
- Useful for protocols like DNS, DHCP, NTP, SNMP, VoIP.
- Example:
    
    ```bash
    nmap -sU 192.168.124.148
    ```
    

---

## 🎛️ Limiting Target Ports

- **Default** → scans 1000 most common ports.
- `-F` → Fast mode (100 most common ports).
- `-p[range]` → specify custom range:
    - `-p10-1024` → ports 10–1024
    - `-p-25` → ports 1–25
    - `-p-` → all ports (1–65535)

---

# 📊 Summary Table

|Option|⚡ Explanation|
|---|---|
|`-sT`|TCP connect scan → full handshake|
|`-sS`|TCP SYN scan → stealthy, partial handshake|
|`-sU`|UDP scan → detects UDP services|
|`-F`|Fast mode → 100 common ports|
|`-p[range]`|Custom port range (e.g., `-p-` for all ports)|

---

# 🎯 Takeaway

- Use **`-sT`** for reliability, **`-sS`** for stealth, **`-sU`** for UDP services.
- Limit ports with **`-F`** or **`-p[range]`** for efficiency.
- Thorough scans → `-p-` (all 65,535 ports).