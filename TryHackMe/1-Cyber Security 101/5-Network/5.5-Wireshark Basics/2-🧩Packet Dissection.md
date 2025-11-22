**Packet dissection (protocol dissection)** = decoding packet details into OSI layers for analysis.  
Wireshark supports many protocols and allows custom dissection scripts.

---

## 📋 Packet Details

- Click on a packet in **Packet List Pane** → opens details
![[Pasted image 20251122140427.png]]
- Double-click → opens in new window
![[Pasted image 20251122142046.png]]
- Each detail highlights corresponding bytes in **Packet Bytes Pane**
- Packets typically show **5–7 OSI layers**

---

# 🏗️ OSI Layer Breakdown in Wireshark

### 1️⃣ Frame (Physical Layer)

- Shows **frame/packet info**
- Physical layer details (size, capture time, etc.)

---

### 2️⃣ Source [MAC] (Data Link Layer)

- Displays **source & destination MAC addresses**
- Identifies devices on local network

---

### 3️⃣ Source [IP] (Network Layer)

- Shows **source & destination IPv4 addresses**
- Maps logical addressing across networks

---

### 4️⃣ Protocol (Transport Layer)

- Indicates **protocol type** (TCP/UDP)
- Displays **source & destination ports**

---

### ⚠️ Protocol Errors (Transport Layer continuation)

- Highlights **TCP reassembly issues**
- Useful for troubleshooting fragmented or retransmitted segments

---

### 5️⃣ Application Protocol (Application Layer)

- Shows **protocol-specific details** (HTTP, FTP, SMB, etc.)
- Decodes headers and metadata

---

### 📦 Application Data (Application Layer extension)

- Displays **payload content** (e.g., HTTP request/response body)
- Reveals actual transmitted data

---

# 📊 Quick Recap Table

|🔢 Layer|🧩 OSI Model|📌 What Wireshark Shows|
|---|---|---|
|1️⃣ Frame|Physical|Frame info, capture details|
|2️⃣ MAC|Data Link|Source & destination MAC|
|3️⃣ IP|Network|Source & destination IP|
|4️⃣ Protocol|Transport|TCP/UDP + ports|
|⚠️ Errors|Transport|TCP reassembly issues|
|5️⃣ App Protocol|Application|HTTP/FTP/SMB headers|
|📦 App Data|Application|Payload content|

---

# 🎯 Takeaway

Wireshark dissects packets into **OSI layers**, allowing analysts to:

- Trace communication flow 🌐
- Spot errors ⚠️
- Investigate protocols 🔎
- Inspect payloads 📦