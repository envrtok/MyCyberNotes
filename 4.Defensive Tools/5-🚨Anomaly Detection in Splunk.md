Now that abnormal log days have been identified, the next step is to drill into specific fields to uncover suspicious activity. Switch back to the **Events** tab for detailed inspection.

---

### 1. **User Agent Analysis**

- Click on the **user_agent** field in the left panel.
- Splunk displays all captured user agents.
- **Observation:** Alongside legitimate agents (e.g., Mozilla variants), there is a **large cluster of suspicious user agents**. These anomalies warrant deeper investigation, as attackers often spoof or use unusual agents during exploitation attempts.
![[Pasted image 20251208154316.png]]

---

### 2. **Client IP Analysis**

- Next, examine the **client_ip** field.
- This shows the IP addresses accessing the web server.
- **Observation:** One IP address clearly stands out due to abnormal activity volume. This IP becomes a prime candidate for correlation with attack behavior.
![[Pasted image 20251208154324.png]]

---

### 3. **Path Analysis**

- Finally, review the **path** field, which contains the URIs requested by clients.
- **Observation:** Certain paths reveal **attack patterns** (e.g., probing unusual endpoints, attempting directory traversal, or exploiting vulnerable routes).
![[Pasted image 20251208154343.png]]

---

## 🎯 Key Takeaways

- **Suspicious user agents** → Possible automated tools or malicious scripts.
- **Outlier client IP** → Likely attacker source.
- **Malicious paths** → Evidence of exploitation attempts.