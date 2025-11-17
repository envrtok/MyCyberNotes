### 📡 `ipconfig`

- `"ipconfig"` gives network information

```cmd
user@WINSRV2022-CORE C:\Users\user>ipconfig

Windows IP Configuration

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : eu-west-1.compute.internal
   Link-local IPv6 Address . . . . . : fe80::9e5:86c4:4159:c64a%5
   IPv4 Address. . . . . . . . . . . : 10.10.138.170
   Subnet Mask . . . . . . . . . . . : 255.255.0.0
   Default Gateway . . . . . . . . . : 10.10.0.1
```

---

### 📡 `ipconfig /all`

- `"ipconfig /all"` → same as ipconfig, but with more details

```cmd
user@WINSRV2022-CORE C:\Users\user>ipconfig /all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : WINSRV2022-CORE
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : eu-west-1.compute.internal
                                       eu-west-1.ec2-utilities.amazonaws.com

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : eu-west-1.compute.internal
   Description . . . . . . . . . . . : Amazon Elastic Network Adapter
   Physical Address. . . . . . . . . : 02-2B-29-51-4E-4F
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::9e5:86c4:4159:c64a%5 (Preferred)
   IPv4 Address. . . . . . . . . . . : 10.10.138.170 (Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.0.0
   Lease Obtained. . . . . . . . . . : Monday, November 17, 2025 1:20:08 PM
   Lease Expires . . . . . . . . . . : Monday, November 17, 2025 2:20:07 PM
   Default Gateway . . . . . . . . . : 10.10.0.1
   DHCP Server . . . . . . . . . . . : 10.10.0.1
   DNS Servers . . . . . . . . . . . : 10.0.0.2
   NetBIOS over Tcpip. . . . . . . . : Enabled
```

---

### 📶 `ping`

- `"ping example.com"` → sends ICMP packets, checks if server is up, and connection info

```powershell
PS C:\> ping google.com

Pinging google.com [172.217.17.142] with 32 bytes of data:
Reply from 172.217.17.142: bytes=32 time=14ms TTL=116
Reply from 172.217.17.142: bytes=32 time=14ms TTL=116
Reply from 172.217.17.142: bytes=32 time=12ms TTL=116
Reply from 172.217.17.142: bytes=32 time=14ms TTL=116

Ping statistics for 172.217.17.142:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 12ms, Maximum = 14ms, Average = 13ms
```

---

### 🛣️ `tracert`

- `"tracert example.com"` → checks connection health using ICMP packets with increasing TTL

```cmd
C:\>tracert example.com

Tracing route to example.com [93.184.215.14] over a maximum of 30 hops:

 1   59 ms   32 ms   42 ms ec2-3-248-240-3.eu-west-1.compute.amazonaws.com [3.248.240.3]
 2   *  *  *  Request timed out.
 ...
 9   <1 ms   13 ms   <1 ms 100.100.2.56
10   15 ms   11 ms   11 ms ae-42.a03.londen12.uk.bb.gin.ntt.net [131.103.117.104]
11   17 ms   11 ms   12 ms ae-14.r20.londen12.uk.bb.gin.ntt.net [129.250.3.248]
12   81 ms   80 ms   80 ms ae-7.r20.nwrknj03.us.bb.gin.ntt.net [129.250.6.147]
13   83 ms   83 ms   86 ms ae-0.a02.nycmny17.us.bb.gin.ntt.net [129.250.3.9]
14   79 ms   79 ms   96 ms ce-0-3-0.a02.nycmny17.us.ce.gin.ntt.net [128.241.1.14]
15   81 ms   86 ms   79 ms ae-67.core1.nyd.edgecastcdn.net [152.195.68.135]
16   78 ms   78 ms   78 ms 93.184.215.14

Trace complete.
```

---

### 🔍 `nslookup`

- `"nslookup example.com"` → gives server and address info

```cmd
C:\>nslookup example.com
Server: ip-10-0-0-2.eu-west-1.compute.internal
Address: 10.0.0.2

Non-authoritative answer:
Name: example.com
Addresses: 2606:2800:21f:cb07:6820:80da:af6b:8b2c
           93.184.215.14

C:\>nslookup example.com 1.1.1.1
Server: one.one.one.one
Address: 1.1.1.1

Non-authoritative answer:
Name: example.com
Addresses: 2606:2800:21f:cb07:6820:80da:af6b:8b2c
           93.184.215.14
```

---

### 🔌 `netstat`

- `"netstat"` → shows using ports
    - `netstat -h` → help
    - `netstat -a` → all established ports
    - `netstat -b` → program using ports
    - `netstat -o` → process PID of port connection
    - `netstat -n` → numerical form
    - ⚡ General usage: `netstat -abon`

```cmd
C:\>netstat -abon

Active Connections

Proto  Local Address     Foreign Address   State       PID
TCP    0.0.0.0:22        0.0.0.0:0         LISTENING   2116 [sshd.exe]
TCP    0.0.0.0:135       0.0.0.0:0         LISTENING   820 RpcSs [svchost.exe]
TCP    0.0.0.0:49669     0.0.0.0:0         LISTENING   2036 [spoolsv.exe]
TCP    0.0.0.0:49670     0.0.0.0:0         LISTENING   584 Can not obtain ownership information
TCP    0.0.0.0:49686     0.0.0.0:0         LISTENING   592 [lsass.exe]
TCP    10.10.230.237:22  10.11.81.126:53486 ESTABLISHED 2116 [sshd.exe]
...
```
