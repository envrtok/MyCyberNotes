`tcpdump` offers multiple options to **customize how packets are printed**. These options help analysts view traffic at different levels of detail.

---

## 🔑 Key Display Options

### 1️⃣ `-q` → Quick Output

- Prints **brief packet info** (timestamp, source/destination IP + ports, length).
- Example:
    
    ```bash
    tcpdump -r TwoPackets.pcap -q
    ```
    

---

### 2️⃣ `-e` → Link-Level Header

- Includes **MAC addresses** in output.
- Useful for ARP, DHCP, or tracking unusual sources.
- Example:
    
    ```bash
    tcpdump -r TwoPackets.pcap -e
    ```
    

---

### 3️⃣ `-A` → ASCII Output

- Displays packet data as **ASCII text** (letters, numbers, symbols).
- Best for plain-text protocols (HTTP, SMTP).
- Example:
    
    ```bash
    tcpdump -r TwoPackets.pcap -A
    ```
    

---

### 4️⃣ `-xx` → Hexadecimal Output

- Shows packet data in **hexadecimal format** (octet by octet).
- Useful for encrypted/compressed data or non-English text.
- Example:
    
    ```bash
    tcpdump -r TwoPackets.pcap -xx
    ```
    

---

### 5️⃣ `-X` → Hex + ASCII

- Displays **both hex and ASCII** side by side.
- Best of both worlds → headers + readable text.
- Example:
    
    ```bash
    tcpdump -r TwoPackets.pcap -X
    ```
    

---

# 📊 Summary Table

|Command|⚡ Explanation|
|---|---|
|`tcpdump -q`|Quick output: brief info|
|`tcpdump -e`|Include MAC addresses|
|`tcpdump -A`|Show packet data in ASCII|
|`tcpdump -xx`|Show packet data in hex|
|`tcpdump -X`|Show packet data in hex + ASCII|

---

# 🎯 Takeaway

- Use **`-q`** for concise summaries
- Use **`-e`** for MAC-level analysis
- Use **`-A`** for text payloads
- Use **`-xx`** for raw hex inspection
- Use **`-X`** for combined readability