Nmap allows analysts to **control scan output** in two main ways:

1. Showing **additional information** during scans (verbosity/debugging).
2. Choosing **file formats** to save scan reports.

---

## 🔎 Verbosity Levels (`-v`)

- Default → minimal output.
- `-v` → verbose (shows scan stages: ARP ping, DNS resolution, SYN scan).
- `-vv`, `-vvvv` → increase verbosity further.
- Direct levels: `-v2`, `-v4`.
- Can press **`v` during scan** to increase verbosity live.

👉 Example:

```bash
nmap -sS 192.168.139.1/24 -v
```

---

## 🐞 Debugging Levels (`-d`)

- Provides **debugging-level output**.
- `-d` → basic debug info.
- `-d9` → maximum debug (thousands of lines).
- Useful for troubleshooting scan behavior.

👉 Example:

```bash
nmap -sS 192.168.139.1/24 -d3
```

---

## 💾 Saving Scan Reports

Nmap supports multiple output formats:

|Option|Format|Use Case|
|---|---|---|
|`-oN <file>`|Normal|Human-readable|
|`-oX <file>`|XML|Structured, machine-readable|
|`-oG <file>`|Grepable|Easy parsing with `grep`/`awk`|
|`-oA <basename>`|All formats|Generates `.nmap`, `.xml`, `.gnmap`|

👉 Example:

```bash
nmap -sS 192.168.139.1 -oA gateway
```

Produces:

- `gateway.nmap` → normal
- `gateway.xml` → XML
- `gateway.gnmap` → grepable

---

# 📊 Quick Recap Table

|Option|⚡ Explanation|
|---|---|
|`-v`|Verbose output (increase with more v’s)|
|`-d`|Debugging output (increase with more d’s, up to `-d9`)|
|`-oN`|Save normal human-readable output|
|`-oX`|Save XML output|
|`-oG`|Save grepable output|
|`-oA`|Save all formats simultaneously|

---

# 🎯 Takeaway

- Use **verbosity (`-v`)** for real-time progress.
- Use **debugging (`-d`)** for troubleshooting.
- Save results with **output options (`-oN`, `-oX`, `-oG`, `-oA`)** for later analysis.