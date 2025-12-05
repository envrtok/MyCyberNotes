Controlling **scan speed** is crucial to balance stealth, accuracy, and efficiency.  
Fast scans may trigger IDS/firewalls, while slow scans reduce detection but take longer.

---

## ⏱️ Timing Templates (`-T<0-5>`)

Nmap offers **six timing modes**:

|Timing|Name|Behavior|Example Duration (100 ports)|
|---|---|---|---|
|`-T0`|Paranoid|Very slow, stealthy|~9.8 hours|
|`-T1`|Sneaky|Slow, avoids detection|~27.5 minutes|
|`-T2`|Polite|Moderate, reduces load|~40.5 seconds|
|`-T3`|Normal|Default speed|~0.15 seconds|
|`-T4`|Aggressive|Faster, riskier|~0.13 seconds|
|`-T5`|Insane|Maximum speed, very noisy|(not shown, but fastest)|

👉 Example usage:

```bash
nmap -sS -F -T2 10.80.157.238
```

---

## ⚡ Parallelism Control

- `--min-parallelism <num>` → minimum probes active
- `--max-parallelism <num>` → maximum probes active
- Nmap adjusts automatically based on network performance.
    - Poor network → fewer probes
    - Reliable network → hundreds of probes possible

---

## 📡 Rate Control

- `--min-rate <number>` → minimum packets/sec
- `--max-rate <number>` → maximum packets/sec
- Applies to **entire scan**, not per host.
- Example:
    
    ```bash
    nmap --min-rate 1000 192.168.1.0/24
    ```
    

---

## ⏳ Host Timeout

- `--host-timeout <time>` → maximum wait time per host
- Useful for **slow/unresponsive hosts**
- Example:
    
    ```bash
    nmap --host-timeout 60s 192.168.1.100
    ```
    

---

# 📊 Summary Table

|Option|⚡ Explanation|
|---|---|
|`-T<0-5>`|Timing templates (paranoid → insane)|
|`--min-parallelism / --max-parallelism`|Control number of parallel probes|
|`--min-rate / --max-rate`|Control packet rate (packets/sec)|
|`--host-timeout`|Max wait time per host|

---

# 🎯 Takeaway

- **Slow scans (T0–T2)** → stealthy, avoid detection, but time-consuming.
- **Fast scans (T3–T5)** → efficient, but noisy and easily detected.
- Fine-tune with **parallelism, rate, and timeout** for optimal performance