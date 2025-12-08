### Step 1: Exclude Legitimate User Agents

Run the following query to filter out requests from common browsers (Mozilla, Chrome, Safari, Firefox):

```
sourcetype=web_traffic user_agent!=*Mozilla* user_agent!=*Chrome* user_agent!=*Safari* user_agent!=*Firefox* 
| stats count by client_ip 
| sort -count 
| head 5
```

- This query lists the **top 5 client IPs** that are sending requests with **non-standard user agents**.
- The `sort -count` ensures results are ordered by event volume in descending order (same effect as `reverse`).
![[Pasted image 20251208154436.png]]

---

### Step 2: Interpret the Results

- The output highlights the **most active suspicious IPs**.
- Among them, one IP clearly dominates — identified as the **primary source used by the Bandit Bunnies**.
- This IP is likely tied to automated tools or malicious scripts rather than normal browsers.

---

### Step 3: Next Action

- Select the **top suspicious IP** from the results.
- Filter the logs specifically for this IP to trace its **footprints** — examining:
    - **Paths accessed** (URIs requested)
    - **User agents used**
    - **Frequency and timing of requests**
    - **Correlation with firewall logs**

---

## 🎯 Key Takeaway

By excluding legitimate browser traffic, we isolate attacker IPs more efficiently. The dominant IP becomes the focal point for deeper forensic analysis, helping confirm the attacker’s behavior and tactics.