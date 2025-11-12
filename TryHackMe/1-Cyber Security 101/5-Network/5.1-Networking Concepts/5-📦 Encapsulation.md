## 🧱 What is Encapsulation?

**Encapsulation** is the process where each layer adds its own **header** (and sometimes **trailer**) to the data unit it receives before passing it down to the next layer below.

Think of it like sending a letter in multiple envelopes:
- 📝 Write your message (Application Data)
- 📮 Put it in an envelope with postal instructions (Transport Header)
- 🏢 Put that in a larger envelope with address info (Network Header)
- 🚚 Finally, package it for physical delivery (Link Header + Trailer)

---

## 🔄 The 4-Step Encapsulation Process

### 1. **Application Data** 📝
- 🎯 **Starts with user input** (email, chat message, search query)
- 📱 Application formats data according to its protocol
- ⬇️ Passes data to **Transport Layer**

### 2. **Transport Layer** 🚚
- 🔧 Adds **TCP or UDP header**
- 🏷️ Includes **source & destination port numbers**
- 📦 Creates a **TCP segment** or **UDP datagram**
- ⬇️ Passes to **Network Layer**

### 3. **Network Layer** 🌐
- 🏷️ Adds **IP header**
- 📍 Includes **source & destination IP addresses**
- 📫 Creates an **IP packet**
- ⬇️ Passes to **Data Link Layer**

### 4. **Data Link Layer** 🔗
- 🏷️ Adds **header & trailer** (e.g., Ethernet frame)
- 📡 Includes **MAC addresses**
- 📦 Creates a **frame**
- ⬇️ Sent over physical network

---

## 🎯 Visualizing Encapsulation

```
Application Data: "Hello World!"
    ↓
TCP Header + "Hello World!" = TCP Segment
    ↓
IP Header + TCP Segment = IP Packet
    ↓
Ethernet Header + IP Packet + Trailer = Frame
```

---

## 📮 Real-World Example: Searching TryHackMe

Let's trace what happens when you search for a room on TryHackMe:

### **On Your Computer:**
1. **📝 Application Layer**: Your browser creates an **HTTP request** with your search query
2. **🚚 Transport Layer**: **TCP** establishes connection (3-way handshake) and adds TCP header
3. **🌐 Network Layer**: **IP** adds your IP and TryHackMe's IP address
4. **🔗 Data Link Layer**: **Ethernet/WiFi** adds MAC addresses and creates frame

### **📦 Journey Through the Network:**
- 🛣️ **Routers** along the way:
  - Remove Link Layer header/trailer
  - Inspect **IP destination**
  - Route packet toward destination
  - Re-encapsulate for next hop

### **🏁 At TryHackMe Server:**
- 🔄 The **reverse process** happens:
  - Remove Link Layer wrapper → IP packet
  - Remove IP header → TCP segment  
  - Remove TCP header → HTTP request
  - Deliver to web server application

---

## 💡 Key Takeaways

- 🎁 **Each layer wraps data** with its own addressing/control information
- 🔄 **Encapsulation happens when sending**, **de-encapsulation when receiving**
- 🛣️ **Routers** only de-encapsulate down to **IP layer** to make routing decisions
- 📧 Like Russian nesting dolls - each layer adds its own container around the data

**In short:** Encapsulation is how data gets dressed up in layers of addressing information to travel across networks! 🎒✈️