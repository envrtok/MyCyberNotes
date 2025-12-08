### 🔎 Identity Found

- The attacker was identified through the **highest volume of malicious web traffic** originating from a specific external IP.

### 🛠 Intrusion Vector

- The attack chain was clearly documented in the **web logs (`sourcetype=web_traffic`)**, showing a step-by-step progression.

### 🕵️ Reconnaissance

- Initial probes were launched using **cURL/Wget**, targeting sensitive configuration files (`/.env`) and attempting **path traversal** vulnerabilities.

### 💉 Exploitation

- Evidence of **SQL injection** was confirmed via:
    - **SQLmap user agents** in the logs.
    - Payloads such as `SLEEP(5)` indicating time-based injection attempts.

### 📦 Payload Delivery

- The **Action on Objective** was achieved when the attacker executed:
    
    ```
    cmd=./bunnylock.bin
    ```
    
- This was done through a **webshell**, confirming **remote code execution (RCE)** and ransomware staging.

### 📡 C2 Confirmation

- Pivoting to the **firewall logs (`sourcetype=firewall_logs`)** revealed post-exploitation activity:
    - The compromised server (`SRC_IP: 10.10.1.5`) established an **outbound connection** to the attacker’s IP.
    - Logs confirmed **C2 communication** was allowed, validating the malware channel was active.

---

## 🎯 Final Assessment

The investigation confirms a **full kill chain compromise**:

1. Reconnaissance → probing configs and vulnerabilities.
2. Exploitation → SQL injection via automated tools.
3. Payload Delivery → ransomware execution through webshell.
4. C2 Communication → outbound connection to attacker infrastructure.
5. Data Exfiltration → confirmed by high-volume transfers.

This sequence demonstrates a **successful intrusion with ransomware staging and C2 control**, requiring immediate containment and eradication measures.