We explored how **Nmap** helps analysts discover hosts, identify services, detect OS versions, control timing, and save results.

---

## 🔎 Host Discovery

- `-sL` → List scan (targets only, no probing)
- `-sn` → Ping scan (find live hosts)
- `-Pn` → Treat all hosts as online (force scan even if silent)

---

## 🔌 Port Scanning

- `-sT` → TCP connect (full handshake)
- `-sS` → TCP SYN (stealthy, partial handshake)
- `-sU` → UDP scan
- `-F` → Fast mode (100 common ports)
- `-p[range]` → Custom port range (`-p-` = all 65,535 ports)

---

## 🧩 Service & OS Detection

- `-O` → OS detection
- `-sV` → enables **service and version detection**, meaning it actively probes open ports with known fingerprints to identify the exact application and version running on each service.
- `--script=banner` → connects to open TCP ports and captures the initial text response (banner) from services to quickly reveal version or service information.
- `-A` → All-in-one (OS + version + traceroute)

---

## ⏱️ Timing & Performance

- `-T0–5` → Timing templates (paranoid → insane)
- `--min-parallelism / --max-parallelism` → Control parallel probes
- `--min-rate / --max-rate` → Control packet rate (packets/sec)
- `--host-timeout` → Max wait time per host

---

## 📡 Real-Time Output

- `-v` → Verbosity (increase with more v’s, e.g., `-vv`)
- `-d` → Debugging (increase with more d’s, up to `-d9`)

---

## 💾 Saving Reports

- `-oN <file>` → Normal human-readable output
- `-oX <file>` → XML structured output
- `-oG <file>` → Grepable output (for parsing)
- `-oA <basename>` → Save all formats (`.nmap`, `.xml`, `.gnmap`)

---

# 🎯 Key Takeaway

- Run Nmap with **sudo/root** for full features (e.g., SYN scans).
- Local user mode defaults to **connect scans** with limited capabilities.
- Nmap = **rich, versatile tool** → we covered essentials, but deeper mastery awaits in dedicated modules.