## 🧱 What is DHCP?

**DHCP (Dynamic Host Configuration Protocol)** automatically provides network settings to devices when they join a network. Think of it as a **network concierge** that gives you everything you need to get online!

### 🎯 Why We Need DHCP:
- 📱 **Mobile devices** change networks frequently
- ⚠️ **Prevents IP conflicts** (two devices with same IP)
- ⏱️ **Saves time** - no manual configuration needed
- 🎯 **Essential for**: Laptops, smartphones, IoT devices

### 🚫 **When NOT to use DHCP:**
- 🖥️ **Servers** need static IPs (always at the same address)
- 🏢 **Network equipment** (routers, switches)
- 📍 **Printers** and shared resources

---

## 🔧 What DHCP Configures

DHCP automatically sets these **4 critical network settings**:

1. **IP Address** 🏠 - Your device's unique network identity
2. **Subnet Mask** 🗺️ - Defines your local network boundaries  
3. **Router/Gateway** 🚪 - The exit door to other networks/Internet
4. **DNS Server** 📞 - Translates domain names to IP addresses

---

## 🔄 The DHCP DORA Process

DHCP follows a **4-step handshake** called **DORA**:

### 1. **Discover** 📢
- 🆕 Device joins network with **no IP config**
- 📢 Broadcasts: **"Is there a DHCP server here?"**
- 🎯 From: `0.0.0.0:68` → To: `255.255.255.255:67`

### 2. **Offer** 🤝  
- 🎁 DHCP server responds: **"Here's an IP you can use!"**
- 📦 Includes: IP address, subnet mask, gateway, DNS
- 🎯 Sent directly to device's MAC address

### 3. **Request** ✅
- 👍 Device responds: **"Yes, I'll take that IP!"**
- 📢 Broadcasts acceptance to all DHCP servers
- 🎯 Prevents multiple servers from thinking device accepted their offer

### 4. **Acknowledge** 🎉
- 🏆 DHCP server confirms: **"IP is yours for now!"**
- ⏰ Includes **lease time** (how long you can keep the IP)
- 🎯 Device now has full network configuration

---

## 📊 Real DHCP Example

```bash
user@TryHackMe$ tshark -r DHCP-G5000.pcap -n
1 0.000000 0.0.0.0 → 255.255.255.255 DHCP 342 DHCP Discover - Transaction ID 0xfb92d53f
2 0.013904 192.168.66.1 → 192.168.66.133 DHCP 376 DHCP Offer - Transaction ID 0xfb92d53f
3 4.115318 0.0.0.0 → 255.255.255.255 DHCP 342 DHCP Request - Transaction ID 0xfb92d53f
4 4.228117 192.168.66.1 → 192.168.66.133 DHCP 376 DHCP ACK - Transaction ID 0xfb92d53f
```

**What happened:**
- 📍 Client got IP address: `192.168.66.133`
- 🏠 DHCP server: `192.168.66.1`
- 🔢 Same **Transaction ID** tracks the conversation

---

## 💡 Key Technical Details

### 🎯 **Protocol & Ports:**
- **Application Layer** protocol
- Uses **UDP** (not TCP)
- **Server** listens on **UDP port 67**
- **Client** uses **UDP port 68**

### 🌐 **Broadcast Behavior:**
- 📢 Initial messages use **IP broadcast** (`255.255.255.255`)
- 📡 **MAC broadcast** (`ff:ff:ff:ff:ff:ff`)
- 🆔 Device starts with **only MAC address**, no IP

### ⏰ **Lease Time:**
- 🕐 IP addresses are **leased**, not given permanently
- 🔄 Devices must **renew** before lease expires
- 📱 Supports **mobile devices** coming/going from network

---

## 🎯 Key Takeaways

- 🤖 **DHCP automates** network configuration
- 🔄 **DORA process**: Discover → Offer → Request → Acknowledge
- 📱 **Essential for mobile devices** - phones, laptops, tablets
- 🖥️ **Not for servers** - they need static IPs
- 🛡️ **Prevents IP conflicts** automatically
- 🌐 **Provides everything needed**: IP, subnet, gateway, DNS

**In short:** DHCP is the friendly network butler that automatically gets your devices online! 🤵‍♂️📱