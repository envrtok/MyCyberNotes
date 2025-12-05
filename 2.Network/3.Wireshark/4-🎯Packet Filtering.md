Wireshark’s **filter engine** helps analysts reduce noise and focus on events of interest.  
Two types of filters:

- 🟢 **Capture Filters** → applied during capture (only store matching packets)
- 🔵 **Display Filters** → applied after capture (show/hide packets in view)

---

## 🧩 Golden Rule

👉 _“If you can click on it, you can filter and copy it.”_  
Wireshark’s GUI allows filtering without writing queries.

---

# 🛠️ Filtering Options

## 1️⃣ Apply as Filter

- Right-click a field → `Analyse → Apply as Filter`
- Wireshark generates query automatically
- Shows only matching packets, hides others
- Status bar shows **total vs displayed packets**

---

## 2️⃣ Conversation Filter

- Filters all packets linked to a conversation (IP + port)
- Useful for tracking **entire flows**
- Menu: `Analyse → Conversation Filter`

---

## 3️⃣ Colourise Conversation

- Highlights linked packets without hiding others
- Overrides existing colouring rules
- Menu: `View → Colourise Conversation`
- Reset via `View → Colourise Conversation → Reset Colourisation`

---

## 4️⃣ Prepare as Filter

- Similar to Apply as Filter, but **does not execute immediately**
- Adds query to filter bar → waits for user to press **Enter** or combine with `.. and/or..`

---

## 5️⃣ Apply as Column

- Adds selected field as a **new column** in Packet List Pane
- Helps compare values across packets
- Menu: `Analyse → Apply as Column`
- Columns can be enabled/disabled at top of Packet List Pane

---

## 6️⃣ Follow Stream

- Reconstructs **application-level traffic** (TCP/UDP/HTTP streams)
- Shows raw data (e.g., usernames, passwords, payloads)
- Packets:
    - 🔵 Server → blue
    - 🔴 Client → red
- Menu: `Analyse → Follow Stream`
- Wireshark auto-applies filter → remove via **X button** in filter bar

---

# 📊 Quick Recap Table

|🧩 Feature|⚡ Purpose|
|---|---|
|**Apply as Filter**|Filter single field value|
|**Conversation Filter**|Show all related packets in a flow|
|**Colourise Conversation**|Highlight linked packets without filtering|
|**Prepare as Filter**|Build query, execute later|
|**Apply as Column**|Add field as column for comparison|
|**Follow Stream**|Reconstruct application-level traffic|

---

# 🎯 Takeaway

Wireshark’s filtering tools = **precision navigation**.

- Use **Apply/Prepare** for single values
- Use **Conversation/Colourise** for flows
- Use **Columns** for comparisons
- Use **Follow Stream** for raw application-level analysis