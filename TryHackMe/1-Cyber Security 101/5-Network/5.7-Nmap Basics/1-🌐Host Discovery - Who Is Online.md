Nmap can discover **live hosts** on a network using different techniques.  
This is the first step before service enumeration or vulnerability scanning.

---

## 🎯 Target Specification

- **IP Range** → `192.168.0.1-10`
- **Subnet** → `192.168.0.1/24` (equivalent to `192.168.0.0-255`)
- **Hostname** → `example.thm`

---

## 🔎 Ping Scan (`-sn`)

- Discovers **hosts online** without scanning services.
- More advanced than simple `ping`.
- Requires **root/sudo** for full capability.
- Example:
    
    ```bash
    nmap -sn 192.168.66.0/24
    ```
    

---

## 🖧 Scanning a Local Network

- Directly connected via Ethernet/WiFi.
- Nmap sends **ARP requests** → replies = “Host is up”.
- Output includes **MAC addresses + vendor info**.
- Example result:
    - `192.168.66.1` → Host up, MAC vendor unknown
    - `192.168.66.88` → Host up, MAC vendor Espressif

---

## 🌍 Scanning a Remote Network

- At least one router separates source and target.
- ARP not possible → Nmap uses:
    - ICMP echo requests
    - ICMP timestamp requests
    - TCP SYN (e.g., port 443)
    - TCP ACK (e.g., port 80)
- Example result:
    - `192.168.11.1` → responded to ICMP echo
    - `192.168.11.2` → no response, marked down

---

## ⚙️ Advanced Host Discovery Options

- `-PS[portlist]` → TCP SYN discovery
- `-PA[portlist]` → TCP ACK discovery
- `-PU[portlist]` → UDP discovery

---

## 📋 List Scan (`-sL`)

- Lists targets **without scanning them**.
- Useful for confirming scope.
- Example:
    
    ```bash
    nmap -sL 192.168.0.1/24
    ```
    

---

# 📊 Quick Recap Table

|Option|⚡ Purpose|
|---|---|
|`-sn`|Ping scan → discover live hosts|
|Local Scan|Uses ARP requests, shows MAC/vendor|
|Remote Scan|Uses ICMP + TCP probes|
|`-PS`|TCP SYN discovery|
|`-PA`|TCP ACK discovery|
|`-PU`|UDP discovery|
|`-sL`|List targets only|

---

# 🎯 Takeaway

- Use **`-sn`** for quick host discovery.
- Local scans rely on **ARP**, remote scans rely on **ICMP/TCP/UDP probes**.
- **MAC vendor info** helps identify device types.
- **List scans (`-sL`)** confirm targets before noisy scans.