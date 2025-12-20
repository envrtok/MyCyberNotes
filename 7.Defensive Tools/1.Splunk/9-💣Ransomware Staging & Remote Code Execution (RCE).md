### Step 1: Investigate Suspicious Paths

Run the following query to detect requests tied to ransomware staging and webshell activity:

```
sourcetype=web_traffic client_ip="<REDACTED>" AND path IN ("*bunnylock.bin*", "*shell.php?cmd=*") 
| table _time, path, user_agent, status
```

![[Pasted image 20251208154804.png]]
- **Purpose:** Identify attempts to execute malicious binaries (`bunnylock.bin`) and webshell commands (`shell.php?cmd=`).
- **Output:** Shows timestamps, requested paths, user agents, and status codes.

---

### Step 2: Interpret the Results

- **Data Staging:** Requests for `/logs.tar.gz` and `/config` confirm the attacker was gathering sensitive archives for **double-extortion** (stealing data before encryption).
- **Webshell Execution:** The presence of `/shell.php?cmd=*` confirms a **successful webshell deployment**.
- **RCE Confirmation:** The attacker gained **full control of the web server**, able to run arbitrary commands remotely.
- **Ransomware Payload:** Execution of `/shell.php?cmd=./bunnylock.bin` indicates a ransomware-like binary was launched, staging encryption and extortion.

---

### Step 3: Key Indicators

- **Webshell (`shell.php`)** → Direct command execution capability.
- **Binary (`bunnylock.bin`)** → Malicious payload consistent with ransomware staging.
- **Sensitive Archives (`logs.tar.gz`, `/config`)** → Evidence of data theft prior to encryption.

---

## 🎯 Key Takeaway

The attacker progressed from reconnaissance and exploitation to **full compromise**:

1. **Staging sensitive data** for exfiltration.
2. **Deploying a webshell** to gain persistent remote access.
3. **Executing ransomware payloads** to lock and extort.