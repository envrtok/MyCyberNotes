We now focus on the **selected attacker IP** to reconstruct their steps chronologically. Replace `<REDACTED>` with the suspicious IP identified earlier.

---

## 1. 🕵️ Reconnaissance (Footprinting)

**Query:**

```
sourcetype=web_traffic client_ip="<REDACTED>" AND path IN ("/.env", "/*phpinfo*", "/.git*") 
| table _time, path, user_agent, status
```

- **Purpose:** Detect probing for sensitive configuration files.
- **Result:** Attacker used **low-level tools** (`curl`, `wget`).
- **Status Codes:** Mostly `404`, `403`, `401` → confirms blocked or non-existent files.
![[Pasted image 20251208154552.png]]

---

## 2. 🔍 Enumeration (Vulnerability Testing)

**Initial Query:**

```
sourcetype=web_traffic client_ip="<REDACTED>" AND path="*..*" OR path="*redirect*"
```

- **Purpose:** Identify path traversal (`../../`) and open redirect attempts.
- **Result:** Shows attacker scanning for vulnerable resources.
![[Pasted image 20251208154607.png]]

**Refined Query (escaping characters):**

```
sourcetype=web_traffic client_ip="<REDACTED>" AND path="*..\/..\/*" OR path="*redirect*" 
| stats count by path
```

- **Purpose:** Count frequency of suspicious paths.
- **Result:** Evidence of **data exfiltration attempts** — attacker tried reading system files via traversal.
- **Key Insight:** Attack escalated from scanning to **active exploitation**.
![[Pasted image 20251208154612.png]]

---

## 3. 💉 SQL Injection Attack

**Query:**

```
sourcetype=web_traffic client_ip="<REDACTED>" AND user_agent IN ("*sqlmap*", "*Havij*") 
| table _time, path, status
```

- **Purpose:** Detect automated SQL injection tools.
- **Result:** Logs confirm use of **sqlmap** and **Havij**.
- **Payloads:** Attack strings like `SLEEP(5)` observed.
- **Status Codes:** `504` → often indicates **successful time-based SQL injection**.
![[Pasted image 20251208154620.png]]
---

## 🎯 Key Takeaways

- **Reconnaissance:** Attacker probed for sensitive configs.
- **Enumeration:** Escalated to path traversal and redirect testing.
- **Exploitation:** Confirmed SQL injection attempts using automated tools.
- **Overall:** Clear progression from **scanning → probing → exploitation**, showing a structured attack chain.