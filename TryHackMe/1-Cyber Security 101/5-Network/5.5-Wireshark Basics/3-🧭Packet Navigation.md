Wireshark provides multiple navigation and annotation tools to help analysts manage **large packet captures** efficiently.

---

## 🔢 Packet Numbers

- Each packet gets a **unique number**
- Helps track events in large captures
- Easy to jump back to specific points

---

## 📌 Go to Packet

- Navigate directly to a packet by number
- Supports **in-frame tracking** → find next packet in a conversation
- Menu: `Go → Go to Packet`

---

## 🔍 Find Packets

- Search packets by **content**
- Menu: `Edit → Find Packet`
- Input types:
    - 🧩 Display filter
    - 🔢 Hex
    - 🔤 String
    - 🔎 Regex
- Case-insensitive by default (can toggle sensitivity)
- Search fields:
    - Packet List Pane
    - Packet Details Pane
    - Packet Bytes Pane  
        ⚠️ Must choose correct pane → otherwise search fails

---

## 🏷️ Mark Packets

- Mark/unmark packets for later review
- Menu: `Edit` or **right-click**
- Marked packets = shown in **black**
- ❗ Marks are session-only → lost after closing file

---

## 💬 Packet Comments

- Add notes to specific packets
- Comments persist in capture file until removed
- Useful for collaboration or highlighting suspicious events
- Right click to packet, choose packet comment

---

## 📤 Export Packets

- Export selected packets for deeper analysis
- Menu: `File → Export Packets`
- Helps share only **relevant/suspicious traffic**

---

## 📦 Export Objects (Files)

- Extract transferred files from streams
- Supported protocols: **DICOM, HTTP, IMF, SMB, TFTP**
- Menu: `File → Export Objects`

---

## ⏱️ Time Display Format

- Default: **Seconds since capture start**
- Common alternative: **UTC Time**
- Menu: `View → Time Display Format`

---

## 🧑‍🔬 Expert Info

- Detects protocol states → highlights anomalies
- Severity levels:
    - 🔵 **Chat** → normal workflow info
    - 🌐 **Note (Cyan)** → notable events (e.g., error codes)
    - ⚠️ **Warn (Yellow)** → unusual codes/problems
    - ❌ **Error (Red)** → malformed packets
- Common groups:
    - ✅ Checksum errors
    - 📝 Comment detection
    - ⚠️ Deprecated protocol usage
    - ❌ Malformed packet detection
- Menu: `Analyse → Expert Information` or status bar (bottom-left)

---

# 📊 Quick Recap Table

|🧩 Feature|⚡ Purpose|
|---|---|
|**Packet Numbers**|Unique IDs for navigation|
|**Go to Packet**|Jump to specific packet/conversation|
|**Find Packets**|Search via filters, hex, string, regex|
|**Mark Packets**|Highlight packets (session-only)|
|**Comments**|Persistent notes in capture file|
|**Export Packets**|Share suspicious traffic only|
|**Export Objects**|Extract transferred files|
|**Time Format**|Adjust capture time display|
|**Expert Info**|Spot anomalies (warn/error/chat/note)|

---

# 🎯 Takeaway

Wireshark’s **navigation & annotation tools** (numbers, search, marks, comments, exports, expert info) make it possible to **efficiently investigate large captures**, highlight anomalies, and collaborate with other analysts.