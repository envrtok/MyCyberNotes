## 🧱 What is TELNET?

**TELNET (Teletype Network)** is a network protocol for **remote terminal connections**. In simple terms:

- 💻 **telnet client** lets you connect to any remote system
- ⌨️ Communicate via **text commands**
- 🎯 Originally for remote administration, but now useful for **testing any TCP service**

---

## 🎯 Three Service Demonstrations

### 1. **Echo Server** (Port 7) 🔄
- 📍 **Listens on TCP port 7**
- 🗣️ **Echoes back** everything you send
- 🔒 *Security Note: Echo servers are considered risks and shouldn't run in production*

**Example:**
```bash
user@TryHackMe$ telnet MACHINE_IP 7
Trying MACHINE_IP...
Connected to MACHINE_IP.
Escape character is '^]'.
Hi
Hi
How are you?
How are you?
Bye
Bye
^] 
telnet> quit
Connection closed.
```

**To close connection:** Press `CTRL + ]` then type `quit`

---

### 2. **Daytime Server** (Port 13) ⏰
- 📍 **Listens on TCP port 13**
- 📅 **Returns current date and time**
- 🔒 *Security Note: Daytime servers are also security risks*

**Example:**
```bash
user@TryHackMe$ telnet MACHINE_IP 13
Trying MACHINE_IP...
Connected to MACHINE_IP.
Escape character is '^]'.
Thu Jun 20 12:36:32 PM UTC 2024
Connection closed by foreign host.
```

**Note:** Connection **automatically closes** after sending the time

---

### 3. **Web Server** (Port 80) 🌐
- 📍 **Listens on TCP port 80**
- 🕸️ **Serves web pages** using HTTP protocol
- 💬 You can **manually send HTTP commands**

**Example:**
```bash
user@TryHackMe$ telnet MACHINE_IP 80
Trying MACHINE_IP...
Connected to MACHINE_IP.
Escape character is '^]'.
GET / HTTP/1.1
Host: telnet.thm

HTTP/1.1 200 OK
Content-Type: text/html
[...]
Connection closed by foreign host.
```

**Key steps for HTTP:**
1. Connect to port 80
2. Send `GET / HTTP/1.1`
3. Send `Host: telnet.thm` 
4. Press **Enter twice** (blank line ends the request)
5. Receive HTTP response

---

## 💡 TELNET Tips & Tricks

### 🎯 **Why Use TELNET?**
- 🧪 **Test any TCP service** manually
- 🔍 **Debug network services** without a fancy client
- 📚 **Learn protocols** by seeing raw communication

### ⚠️ **Security Warning**
- 🔓 **TELNET is unencrypted** - passwords sent in clear text!
- 🚫 **Don't use for sensitive connections**
- ✅ Prefer **SSH** for secure remote access

### 🛠️ **Practical Uses Today**
- 🧪 Testing if a port is open
- 🔍 Debugging web servers
- 📡 Checking custom TCP services
- 🎓 Learning how protocols work at the raw level

---

## 🎯 Key Takeaways

- 🔌 **TELNET** can connect to **any TCP port**, not just port 23
- ⌨️ You can **manually communicate** with various services
- 📋 Different protocols require **different commands**:
  - **Echo**: Just type and see it echoed back
  - **Daytime**: Automatically responds with time
  - **HTTP**: Send proper HTTP commands like `GET`
- 🔒 **Always consider security** - these demo services are risky in production

**In short:** TELNET is your Swiss Army knife for testing and understanding TCP services! 🛠️🌐