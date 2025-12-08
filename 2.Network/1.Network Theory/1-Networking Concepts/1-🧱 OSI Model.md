## 🧱 What is the OSI Model?

The **OSI Model (Open Systems Interconnection)** provides a universal framework for **how devices on a network send and receive data**.

---

### 🎯 Why is it Important?

- 🌍 Devices can be from different manufacturers and use different systems.
- 🔄 Thanks to the OSI model, **data communication becomes standardized**; everyone can understand each other.
- 📦 Thanks to this model, data is **processed, sent, and received layer by layer**.

---

### 🧩 How Many Layers Does the OSI Model Have?

The OSI model consists of a total of **7 layers**:

1.  **Physical**
2.  **Data Link**
3.  **Network**
4.  **Transport**
5.  **Session**
6.  **Presentation**
7.  **Application**

➡️ As data passes through the **layers, it is processed and information is added**.
This process is called **encapsulation** and will be detailed in upcoming topics.

---

🧠 **In Summary:**
The **OSI model** standardizes network communication across 7 layers.
Data undergoes separate processes and is encapsulated at each layer.
This allows different systems to communicate with each other seamlessly.

---
## 1️⃣ Physical Layer

📍 This is the bottom layer of the OSI model and one of the easiest to understand.
This layer deals with **the physical components of the hardware** — meaning it's where data is transmitted as **electrical, optical, or radio signals**.

---

#### ⚡ What does it do?

- 💡 Transmits data as **1s and 0s** (binary system)
- 🔌 Cables, connectors, voltage levels, signal types are in this layer
- 🧲 Represents the actual physical connections

---

#### 🖧 Example Components:

- 🧵 Ethernet cable (CAT5/CAT6)
- 📡 Fiber optic cables
- 🧲 Radio signals (Wi-Fi)
- 🔌 Hub, repeater, ports

---

🧠 **Encapsulation:**
At this layer, data is converted into a **bit stream** and transmitted over the physical medium.

---

🔧 **In Short:**
The Physical layer is the answer to the question, "how do we send data physically?"
It is the hardware itself: if you can see the cable, you're at this layer! 👀

---

## 2️⃣ Data Link Layer

🔗 This layer ensures data is **physically transmitted to the correct device on the network**.
It directs communication using the **MAC addresses** of devices within the network.

---

#### 🎯 What is its purpose?

- 📦 Takes **packets** from the Network Layer and adds physical address information (MAC).
- 📍 Each device has a **unique MAC address** embedded in its **Network Interface Card (NIC)** hardware.
- 📡 When data is sent, the target device is identified by its **MAC address, not IP**.
- 📋 Puts the data into a form suitable for transmission.

---

#### 🧪 Example Protocols and Components:

- 🔁 Ethernet
- 🔧 ARP (Matches MAC address with IP)
- 🧲 Switches operate at this layer

---

#### 🧪 Encapsulation:
MAC addresses and error control information are added to the packet → A **Frame** is formed.

---

🧠 **Note:**
MAC addresses are written by the manufacturer (burned-in) and cannot be changed... but they can be **spoofed** 🕵️‍♂️

---

📌 **In Short:**
This layer solves the question, "which physical device on this network should I send this data to?"
Forget IP, **the address here is MAC!**

---

## 3️⃣ Network Layer

🌐 The Network Layer is the layer that **determines the path data will take to reach its destination**.
Things get a bit magical here because data is **routed** and **reassembled**.

---

#### 🚦 What is its purpose?

- 📍 Ensures packets reach the destination using **IP addresses**.
- 🗺️ Selects the **best, shortest, most reliable** path.
- 📦 Determines the route data will take across the network (routing).
- 💡 Routing between devices occurs here.

---

#### 🧭 How does it decide the Route?

- 🛣️ Which is the shortest path? (goes through fewer devices)
- 🔁 Which path has the least data loss?
- ⚡ Which path has a higher physical connection speed? (e.g., fiber vs. copper)

🔀 Some protocols that make these decisions:

- 🧮 OSPF (Open Shortest Path First)
- 🧾 RIP (Routing Information Protocol)

*Knowing their names is enough for now.*

---

#### 📦 Devices and Addresses

- 📡 IP addresses (e.g., `192.168.1.100`) are used at this layer.
- 🛜 Devices that perform routing are called **routers** → **Layer 3 devices**

---

#### 🧪 Encapsulation:
An IP header is added to the segment → A **Packet** is formed.

---

📌 **In Short:**
The Network Layer **knows how the packet will reach its destination and selects the routes.**
This is the domain of routers! 🛰️📦

---

## 4️⃣ Transport Layer

🚚 The Transport Layer ensures data reaches the destination device **correctly, completely, and in order**.
This layer uses one of two main protocols for data transmission: **TCP** or **UDP**.

---

### 🔁 TCP (Transmission Control Protocol)

🔒 Based on **reliability**.
Guarantees data arrives correctly, completely, and in sequence.

#### ✅ Advantages:
- 📦 Ensures data arrives correctly.
- 🔄 Has error checking and retransmission mechanisms.
- 🕓 Establishes a stable connection between devices.

#### ❌ Disadvantages:
- 🐢 Slower than other protocols.
- 🔗 If the connection drops, data is lost and it needs to reconnect.
- 🧩 If every piece of data isn't received, the entire data is considered invalid.

#### 📌 Use Cases:
- 💾 File transfer (FTP)
- 📧 Email (SMTP)
- 🌐 Web browsing (HTTP/HTTPS)

---

### 🚀 UDP (User Datagram Protocol)

🎲 Operates on a "if it arrives, great; if not, no big deal" logic.
It is **connectionless, fast, and uncontrolled**.

#### ✅ Advantages:
- ⚡ Very fast.
- 🧩 Ideal for small data.
- 📱 Loss-tolerant for areas like audio/video streaming.

#### ❌ Disadvantages:
- 📭 Data loss can occur; it is not checked.
- 🚫 No error checking.
- ❌ Does not guarantee sequencing.

#### 📌 Use Cases:
- 🎥 Video streaming (YouTube, Netflix, etc.)
- 📡 Real-time applications (VoIP, online games)
- 🔍 Device discovery protocols (ARP, DHCP)

---

#### 🧪 Encapsulation:
A **TCP** or **UDP** header is added to the data → A **Segment** is formed.

---

📌 **In Short:**
The Transport Layer answers the question for data communication: **speed or accuracy?**
**TCP → reliable but slow**
**UDP → fast but careless** 😎

---
## 5️⃣ Session Layer

🕓 The Session Layer **establishes, manages, and terminates the connection** between two devices.
Before data transmission begins, a **session** is initiated; communication continues as long as this session remains open.

---

#### 🎯 What is its purpose?

- 🔗 Establishes and manages the **connection (session)** between devices.
- 🛑 Terminates connections that are inactive for a long time.
- 🧠 Adds "checkpoints" so that in case of data loss, only the missing part is retransmitted.
- 📶 Each session is **unique** — data only travels over that session.

---

#### 🧪 Encapsulation:
No new header is directly added to the data here, but session management is performed → **Open, controlled data flow** is provided.

---

📌 **In Short:**
The Session Layer solves the question, "**With whom, when, and for how long will I share this data?**"
It establishes, maintains, and closes the connection when the time comes. 🔐📞

---

## 6️⃣ Presentation Layer

🎨 This layer is responsible for **standardizing and converting data**.
Even if there are different software applications, all data must be understood in the same format — the magic that makes this happen is done by this layer!

---

#### 🔁 What is its purpose?

- 🌐 Performs **translation** during data exchange with the application layer.
- 📬 Ensures different software applications can understand each other (e.g., different email apps).
- 🔐 **Encryption and security operations** occur at this layer (e.g., HTTPS).

---

#### 🛠️ Example Tasks:

- 🧩 Converting data formats (JPEG ⇄ PNG, TXT ⇄ DOC)
- 🔐 Encrypting or decrypting data (SSL/TLS, HTTPS)
- 🧬 Compressing data (ZIP, GZIP)

---

#### 🧪 Encapsulation:
At this layer, data is **formatted, encrypted, or converted** → It becomes **ready for presentation**.

---

📌 **In Short:**
The Presentation Layer answers the question, "**How should this data look?**"
It prepares, translates, and secures the data. 🧠🔐

---

## 7️⃣ Application Layer

🧑‍💻 This is the layer with which the **user directly interacts**.
Services we use daily, like email, web browsers, and file-sharing applications, operate at this layer.

---

#### 🎯 What is its purpose?

- 📡 Determines **how data will appear and be used**.
- 🖥️ Presented to the user through **Graphical User Interfaces (GUI)**.
- 🧭 Resolves address lookups on the internet (e.g., DNS).

---

#### 🌐 Example Protocols:

- 📧 SMTP, POP3, IMAP → email sending/receiving
- 🌐 HTTP, HTTPS → accessing web pages
- 🗂️ FTP, SFTP → file transfer
- 🌍 DNS → converts domain names to IP addresses

---

#### 🧪 Encapsulation:
At this layer, user data is received and prepared for transmission to lower layers → It is initiated as **Data**.

---

📌 **In Short:**
The Application Layer answers the question, "**How will the user see and interact with the data?**"
This is your world! 🌍📱💻

---

## 🧠 Mnemonic Sentence:

> **"Please Do Not Throw Sausage Pizza Away"** 🍕
> Physical → Data Link → Network → Transport → Session → Presentation → Application

---

## 🧭 Summary:

The OSI model organizes network communication into **7 layers**,
regulating 📤 how data is sent and
📥 correctly received on the other end.
Data acquires another capsule at each layer and is finally decapsulated on the other end in the correct order.