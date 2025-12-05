After discovering **open ports**, Nmap can identify the **OS type** and **service versions** running on hosts.  
This provides deeper insight into the target system.

---

## 🖥️ OS Detection (`-O`)

- Uses multiple indicators to **guess target OS**.
- Example:
    
    ```bash
    nmap -sS -O 192.168.124.211
    ```
    
- Output:
    - Device type → general purpose
    - Running → Linux 4.x–5.x
    - OS details → Linux 4.15–5.8
- ⚠️ Not perfectly accurate → educated guess only.

---

## ⚡ Service & Version Detection (`-sV`)

- Identifies **service name + version** on open ports.
- Example:
    
    ```bash
    nmap -sS -sV 192.168.124.211
    ```
    
- Output:
    - Port 22 → OpenSSH 8.9p1 Ubuntu (protocol 2.0)
    - Service Info → OS: Linux

---

## 🧩 Combined Scan (`-A`)

- Enables **OS detection + version detection + traceroute + extras**.
- Example:
    
    ```bash
    nmap -A 192.168.124.211
    ```
    

---

## 🚨 Forcing the Scan (`-Pn`)

- Treats **all hosts as online**, even if they don’t respond to ICMP.
- Useful when hosts block ping requests.
- Example:
    
    ```bash
    nmap -Pn -sS 192.168.124.211
    ```
    

---

# 📊 Summary Table

|Option|⚡ Explanation|
|---|---|
|`-O`|OS detection|
|`-sV`|Service + version detection|
|`-A`|OS detection + version detection + traceroute|
|`-Pn`|Force scan hosts marked down|

---

# 🎯 Takeaway

- **`-O`** → OS fingerprinting
- **`-sV`** → Service/version info
- **`-A`** → All-in-one (OS + version + traceroute)
- **`-Pn`** → Scan even “silent” hosts