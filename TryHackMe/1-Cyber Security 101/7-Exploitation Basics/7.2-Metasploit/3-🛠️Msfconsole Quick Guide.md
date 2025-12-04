- 💻 **msfconsole** → opens the Metasploit console
- 📖 **help set** → opens help page
- ⏮️ **history** → shows previous commands
- 🔍 **search** → searches modules
- 🗂️ **search type:\<moduletype> → searches module by type
- 📦 **use** → loads a module into msfconsole
- ℹ️ **info** → shows current payload info
- ↩️ **back** → quits the module

---

## 📋 Show Commands Behavior

|🧾 Command|🌐 Outside a Module|📂 Inside a Module|
|---|---|---|
|**show payloads**|📜 Lists **all payloads globally**|🎯 Lists only **payloads compatible with the current exploit**|
|**show options**|🚫 Nothing useful (no active module)|⚙️ Shows **required/optional settings** (e.g. RHOSTS, LHOST, PAYLOAD)|
|**show advanced**|🚫 Nothing useful|🔧 Shows **advanced options** (timeouts, retries, etc.)|
|**show targets**|🚫 Nothing useful|🎯 Shows **specific target systems** the current exploit can attack|
|**show missing**|🚫 Nothing useful|❗ Lists **required options not set yet** for the current module|

---

## 📚 Other Show Commands

- 🛡️ `show exploits` → all exploit modules
- 🧩 `show auxiliary` → all auxiliary modules
- 🔑 `show encoders` → all encoders
- 🕵️ `show evasion` → all evasion modules
- 🌀 `show nops` → all NOP generators
- 🛠️ `show post` → all post-exploitation modules

---

## ⚙️ Configuring a Module

- ⚙️ **show options** → shows all options of the module
- ✍️ **set \<option> \<input>** → configures the option with given input
- 🗑️ **unset all** → deletes all configurations
- 🎯 **exploit** → starts the listening payload
- 🌀 **exploit -z** → runs exploit & backgrounds session immediately
- 📥 **background** → backgrounds the current session
- 📋 **sessions** → lists all sessions
- 🔗 **sessions -i \<number>** → connects to chosen session