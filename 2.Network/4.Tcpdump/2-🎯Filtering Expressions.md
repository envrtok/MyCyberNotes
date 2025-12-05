Filtering = **focus on specific traffic** instead of capturing everything.  
Think of it like listening to one conversation in a noisy room.

---

## 🧩 Filtering by Host

- Capture packets exchanged with a specific host:
    - `tcpdump host IP`
    - `tcpdump host HOSTNAME`
- Source-only: `tcpdump src host IP`
- Destination-only: `tcpdump dst host IP`
- Example:
    
    ```bash
    sudo tcpdump host example.com -w http.pcap
    ```
    

---

## 🔢 Filtering by Port

- Capture packets on a specific port:
    - `tcpdump port PORT_NUMBER`
- Source port: `tcpdump src port PORT_NUMBER`
- Destination port: `tcpdump dst port PORT_NUMBER`
- Example (DNS traffic on port 53):
    
    ```bash
    sudo tcpdump -i ens5 port 53 -n
    ```
    

---

## 🌐 Filtering by Protocol

- Limit capture to protocol type:
    - `tcpdump ip` → IPv4
    - `tcpdump ip6` → IPv6
    - `tcpdump udp` → UDP
    - `tcpdump tcp` → TCP
    - `tcpdump icmp` → ICMP (ping/traceroute)
- Example:
    
    ```bash
    sudo tcpdump -i ens5 icmp -n
    ```
    

---

## ⚖️ Logical Operators

- Combine filters for precision:
    - `and` → both conditions true
        - `tcpdump host 1.1.1.1 and tcp`
    - `or` → either condition true
        - `tcpdump udp or icmp`
    - `not` → exclude condition
        - `tcpdump not tcp`

---

# 📊 Summary Table

|Command|⚡ Explanation|
|---|---|
|`tcpdump host IP/HOSTNAME`|Filter by host|
|`tcpdump src host IP`|Source host only|
|`tcpdump dst host IP`|Destination host only|
|`tcpdump port PORT_NUMBER`|Filter by port|
|`tcpdump src port PORT_NUMBER`|Source port only|
|`tcpdump dst port PORT_NUMBER`|Destination port only|
|`tcpdump PROTOCOL`|Filter by protocol (ip, ip6, udp, tcp, icmp)|

---

## 🧪 Examples

- SSH traffic:
    
    ```bash
    tcpdump -i any tcp port 22
    ```
    
- NTP traffic on WiFi:
    
    ```bash
    tcpdump -i wlo1 udp port 123
    ```
    
- HTTPS traffic with example.com:
    
    ```bash
    tcpdump -i eth0 host example.com and tcp port 443 -w https.pcap
    ```
    
- Read from file (first 5 packets, no DNS resolution):
    
    ```bash
    tcpdump -r traffic.pcap -c 5 -n
    ```
    
- Count packets from source IP:
    
    ```bash
    tcpdump -r traffic.pcap src host 192.168.124.1 -n | wc
    ```
    

---

# 🎯 Takeaway

- **Host filters** → focus on specific machines
- **Port filters** → focus on services
- **Protocol filters** → focus on traffic type
- **Logical operators** → combine/exclude conditions for precision