When dealing with **thousands/millions of packets**, advanced filters help analysts isolate **precise traffic patterns**.

---

## 📏 Length-Based Filters

- `greater LENGTH` → packets ≥ specified length
- `less LENGTH` → packets ≤ specified length
- Example:
    
    ```bash
    tcpdump greater 100
    tcpdump less 64
    ```
    

---

## ⚙️ Binary Operations Refresher

Binary ops = bitwise logic on header bytes.

- `&` (AND) → true only if both bits = 1
- `|` (OR) → true if at least one bit = 1
- `!` (NOT) → inverts bit (1 → 0, 0 → 1)

---

## 📦 Header Byte Filters

Syntax:

```bash
proto[expr:size]
```

- **proto** → protocol (arp, ether, icmp, ip, ip6, tcp, udp)
- **expr** → byte offset (0 = first byte)
- **size** → number of bytes (default = 1)

### Examples (from `man pcap-filter`):

- `ether[0] & 1 != 0` → packets sent to multicast address
- `ip[0] & 0xf != 5` → IP packets with options

---

## 🚩 Filtering by TCP Flags

Use `tcp[tcpflags]` to reference TCP flag field.  
Available flags:

- 🔑 `tcp-syn` → Synchronize
- 📬 `tcp-ack` → Acknowledge
- 🏁 `tcp-fin` → Finish
- ❌ `tcp-rst` → Reset
- 📦 `tcp-push` → Push

### Examples:

- Only SYN set:
    
    ```bash
    tcpdump "tcp[tcpflags] == tcp-syn"
    ```
    
- At least SYN set:
    
    ```bash
    tcpdump "tcp[tcpflags] & tcp-syn != 0"
    ```
    
- SYN or ACK set:
    
    ```bash
    tcpdump "tcp[tcpflags] & (tcp-syn|tcp-ack) != 0"
    ```
    

---

# 📊 Quick Recap Table

|🧩 Filter Type|⚡ Syntax Example|📌 Purpose|
|---|---|---|
|**Length**|`greater 100`|Packets ≥ 100 bytes|
|**Length**|`less 64`|Packets ≤ 64 bytes|
|**Header Byte**|`ether[0] & 1 != 0`|Multicast packets|
|**Header Byte**|`ip[0] & 0xf != 5`|IP packets w/ options|
|**TCP Flags**|`tcp[tcpflags] == tcp-syn`|Only SYN packets|
|**TCP Flags**|`tcp[tcpflags] & tcp-syn != 0`|SYN packets (flag set)|
|**TCP Flags**|`tcp[tcpflags] & (tcp-syn\|tcp-ack) != 0`|SYN or ACK packets|

---

# 🎯 Takeaway

Advanced filtering = **precision targeting**.

- Length filters → size-based traffic
- Header byte filters → protocol-specific bits
- TCP flag filters → handshake/control packet analysis