`tcpdump` = command-line packet capture tool.  
Useful for **network troubleshooting, protocol analysis, and security investigations**.

---

## 🛠️ Key Options

### 🎛️ Specify Interface

- `-i INTERFACE` → capture on specific interface (e.g., `eth0`, `ens5`)
- `-i any` → capture on all interfaces
- Check interfaces: `ip a s`

---

### 💾 Save Captured Packets

- `-w FILE` → write packets to `.pcap` file
- Example: `tcpdump -i wlo1 -w data.pcap`
- ⚠️ Packets won’t display live when using `-w`

---

### 📂 Read Captured Packets

- `-r FILE` → read packets from file
- Useful for protocol study or attack analysis
- Example: `tcpdump -r data.pcap`

---

### 🔢 Limit Packet Count

- `-c COUNT` → capture only specified number of packets
- Example: `tcpdump -i eth0 -c 50`

---

### 🚫 Disable Resolution

- `-n` → don’t resolve IPs to domain names
- `-nn` → don’t resolve IPs **and** ports to services
- Example: `tcpdump -i ens5 -c 5 -n`

---

### 📣 Verbose Output

- `-v` → more details (TTL, ID, length, options)
- `-vv` → even more verbose
- `-vvv` → maximum verbosity
- Example: `tcpdump -i eth0 -c 50 -v`

---

# 📊 Summary Table

|Command|⚡ Explanation|
|---|---|
|`tcpdump -i IFACE`|Capture packets on interface|
|`tcpdump -w FILE`|Save packets to file|
|`tcpdump -r FILE`|Read packets from file|
|`tcpdump -c COUNT`|Limit number of packets|
|`tcpdump -n`|Disable DNS resolution|
|`tcpdump -nn`|Disable DNS + port resolution|
|`tcpdump -v`|Verbose output (`-vv`, `-vvv` for more)|

---

# 🧪 Examples

- `tcpdump -i eth0 -c 50 -v` → capture 50 packets on `eth0`, verbose output
- `tcpdump -i wlo1 -w data.pcap` → capture on WiFi, save to file
- `tcpdump -i any -nn` → capture on all interfaces, no resolution

---

# 🎯 Takeaway

- Always **specify interface**
- Use `-w` for later analysis in Wireshark
- Use `-r` for replaying captures
- Control verbosity & resolution for clarity