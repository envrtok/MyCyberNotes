Wireshark = **powerful traffic analyzer**. It reads packets deeply but does **not** act as an IDS (Intrusion Detection System). Analysts must interpret anomalies themselves.

---

## 🎯 Use Cases

- 🔧 **Network troubleshooting** → detect congestion, load failures
- 🛡️ **Security anomaly detection** → rogue hosts, abnormal ports, suspicious traffic
- 📚 **Protocol investigation** → response codes, payloads, headers

⚠️ Note: Wireshark only **reads packets**; no modification.

---

## 🖥️ GUI Overview

Wireshark opens with a **single all-in-one page**. Key sections:

- 🛠️ **Toolbar** → menus & shortcuts (filtering, sorting, exporting, merging)
- 🔎 **Display Filter Bar** → main query/filter section
- 📂 **Recent Files** → quick access to past PCAPs
- 🌐 **Capture Filter & Interfaces** → sniffing points (e.g., `lo`, `eth0`, `ens33`)
- 📊 **Status Bar** → tool status, profile, packet counts

![[Pasted image 20251122135444.png]]

---

## 📂 Loading PCAP Files

- Methods: **File → Open**, drag & drop, or double-click
- Once loaded → shows filename, packet count, and details in **3 panes**:

|Pane|Purpose|
|---|---|
|📋 **Packet List**|Summary (src/dst, protocol, info)|
|🔍 **Packet Details**|Protocol breakdown of selected packet|
|💾 **Packet Bytes**|Hex + ASCII representation|
![[Pasted image 20251122135551.png]]

---

## 🎨 Colouring Packets

- Helps spot anomalies quickly
- Two types:
    - ⏳ **Temporary rules** → session-only
    - 📁 **Permanent rules** → saved in profile
- Menus:
    - `View → Coloring Rules` → permanent
    - `View → Conversation Filter` → temporary
- Default colouring highlights protocols (often green).

![[Pasted image 20251122135652.png]]

---

## 📡 Traffic Sniffing

- 🔵 Shark button → start capture
- 🔴 Red button → stop capture
- 🟢 Green button → restart capture
- Status bar → shows interface + packet count

![[Pasted image 20251122135832.png]]

---

## 🔗 Merging PCAP Files

- Path: `File → Merge`
- Select second file → shows packet count
- Click **Open** → merges into new PCAP
- ⚠️ Must save merged file before analysis

---

## 📑 Viewing File Details

- Useful for multiple PCAPs (hash, time, comments, interface, stats)
- Path: `Statistics → Capture File Properties` or bottom-left **PCAP icon**

---

# 📊 Quick Recap Table

|🧩 Feature|⚡ Purpose|
|---|---|
|**Use Cases**|Troubleshooting, security, protocol learning|
|**GUI Sections**|Toolbar, Filter Bar, Recent Files, Interfaces, Status Bar|
|**PCAP Loading**|Packet List, Details, Bytes|
|**Colouring**|Spot anomalies via rules|
|**Sniffing**|Start/stop/restart capture|
|**Merge Files**|Combine PCAPs into one|
|**File Details**|Metadata & statistics|

---

# 🎯 Takeaway

Wireshark = **deep packet analysis tool**. Mastering its GUI (filters, panes, colouring, sniffing, merging) allows analysts to **troubleshoot networks, detect anomalies, and study protocols efficiently**.