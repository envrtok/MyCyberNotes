### Step 1: Pivot to Firewall Logs

Run the following query to trace outbound traffic from the compromised server (`10.10.1.5`) to the attacker’s IP:

```
sourcetype=firewall_logs src_ip="10.10.1.5" AND dest_ip="<REDACTED>" AND action="ALLOWED" 
| table _time, action, protocol, src_ip, dest_ip, dest_port, reason
```

- **Purpose:** Identify whether the compromised server initiated communication with the attacker’s Command & Control (C2) infrastructure.
- **Output:** Displays timestamp, action, protocol, source/destination IPs, destination port, and reason.
![[Pasted image 20251208154917.png]]
---

### Step 2: Interpret the Results

- **Outbound Connection:** The server (`10.10.1.5`) established a connection to the attacker’s IP.
- **Suspicious Port:** The `dest_port` value highlights the port used for C2 traffic.
- **Action Allowed:** `ACTION=ALLOWED` confirms the firewall permitted the connection.
- **Reason Code:** `REASON=C2_CONTACT` explicitly identifies the traffic as malware-related C2 communication.

---

### Step 3: Key Indicators

- **Compromised Host:** 10.10.1.5 (the web server).
- **Attacker IP:** `<REDACTED>` (previously identified).
- **C2 Channel Active:** Outbound traffic allowed on suspicious port.
- **Confirmation:** Firewall logs validate that the malware successfully established its communication channel.

---

## 🎯 Key Takeaway

This correlation proves the **final stage of compromise**: the infected server not only executed malicious payloads but also **connected to the attacker’s C2 infrastructure**, enabling remote control and data exfiltration.