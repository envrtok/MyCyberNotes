### Step 1: Run the Query

Use the `sum` function on the `bytes_transferred` field to calculate total outbound data:

```
sourcetype=firewall_logs src_ip="10.10.1.5" AND dest_ip="<REDACTED>" AND action="ALLOWED" 
| stats sum(bytes_transferred) by src_ip
```

- **Purpose:** Aggregate the total number of bytes sent from the compromised server (`10.10.1.5`) to the attacker’s IP.
- **Output:** Displays the cumulative data volume exfiltrated.
![[Pasted image 20251208155017.png]]
---

### Step 2: Interpret the Results

- **Observation:** The query confirms a **large volume of data** was transferred.
- **Context:** Since the traffic was marked as `ALLOWED`, the firewall did not block the exfiltration.
- **Implication:** The attacker successfully siphoned off compressed archives and logs to their C2 server.

---

### Step 3: Key Indicators

- **src_ip:** 10.10.1.5 (compromised webserver).
- **dest_ip:** `<REDACTED>` (attacker’s C2).
- **bytes_transferred:** High cumulative value → evidence of bulk data theft.

---

## 🎯 Key Takeaway

This confirms the **exfiltration phase of the kill chain**: the attacker not only staged sensitive files but also **moved them out of the environment in bulk**. The sheer volume of transferred data highlights the severity of the compromise.