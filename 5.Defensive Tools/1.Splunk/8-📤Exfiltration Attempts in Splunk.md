### Step 1: Search for Large File Downloads

Run the following query to detect attempts to access backups or log archives:

```
sourcetype=web_traffic client_ip="<REDACTED>" AND path IN ("*backup.zip*", "*logs.tar.gz*") 
| table _time, path, user_agent
```

- **Purpose:** Identify suspicious requests targeting compressed, sensitive files.
- **Output:** Displays timestamp, requested path, and user agent for each attempt.
![[Pasted image 20251208154711.png]]
---

### Step 2: Interpret the Results

- **Observation:** Attacker activity shows requests for `backup.zip` and `logs.tar.gz`.
- **Tools Used:** Indicators point to automated downloaders such as **curl**, **zgrab**, and similar utilities.
- **Implication:** This confirms the attacker moved into the **exfiltration phase**, attempting to pull large chunks of data off the server.

---

### Step 3: Correlate with Firewall Logs

- Cross-reference the suspicious connections in **firewall_logs**.
- This helps confirm whether the outbound traffic was allowed, blocked, or throttled.
- Key details to verify:
    - **Source IP** (attacker)
    - **Destination port/protocol** (HTTP/HTTPS)
    - **Connection status** (allowed/denied)

---

## 🎯 Key Takeaway

The attacker escalated from reconnaissance and exploitation to **data exfiltration**, targeting compressed archives. Firewall correlation is essential to validate whether these attempts succeeded or were blocked.