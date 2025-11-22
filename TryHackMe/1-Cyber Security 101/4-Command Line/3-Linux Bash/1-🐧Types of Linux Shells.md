Linux shells are like **Command Prompt** or **PowerShell** in Windows, but with more variety and flexibility. Each shell has unique features that make it suitable for different tasks.

---

## 🔍 Checking Your Current Shell

- Command: `echo $SHELL` → shows the shell in use
- Example: `/bin/bash`

---

## 📂 Listing Available Shells

- File: `/etc/shells` contains installed shells
- Command: `cat /etc/shells`
- Example output:
    - `/bin/sh`
    - `/bin/bash`
    - `/usr/bin/bash`
    - `/bin/zsh`
    - `/usr/bin/zsh`
    - `/usr/bin/tmux`
    - `/usr/bin/screen`

---

## 🔄 Switching Shells

- Temporary switch: type shell name (e.g., `zsh`)
- Permanent change: `chsh -s /usr/bin/zsh`

---

# 🖥️ Major Linux Shells

## 🟢 Bourne Again Shell (Bash)

- Default in most Linux distros
- Enhanced replacement for older shells (`sh`, `ksh`, `csh`)
- ✨ Features:
    - Powerful scripting
    - Tab completion
    - Command history (`↑ ↓` keys, `history` command)

---

## 🐟 Friendly Interactive Shell (Fish)

- Focuses on **user-friendliness**
- ✨ Features:
    - Simple syntax (great for beginners)
    - Auto spell correction
    - Customizable prompts & themes
    - Built-in syntax highlighting
    - Supports scripting, tab completion, and history

---

## 🦓 Z Shell (Zsh)

- Modern shell, not default in most distros
- ✨ Features:
    - Advanced tab completion
    - Auto spell correction
    - Extensive customization (via **oh-my-zsh**)
    - Command history
    - Plugin support for syntax highlighting

---

# 📊 Comparison Table

|⚡ Feature|🟢 Bash (Bourne Again)|🐟 Fish (Friendly Interactive)|🦓 Zsh (Z Shell)|
|---|---|---|---|
|**Full Name**|Bourne Again Shell|Friendly Interactive Shell|Z Shell|
|**Scripting**|Widely compatible|Limited|Excellent, extended|
|**Tab Completion**|Basic|Advanced suggestions|Plugin-extended|
|**Customization**|Basic|Good via tools|Advanced (oh-my-zsh)|
|**User Friendliness**|Traditional, familiar|Most user-friendly|Highly user-friendly w/ customization|
|**Syntax Highlighting**|❌ Not available|✅ Built-in|⚡ Plugins needed|

---

# 🎯 Choosing the Best Shell

- **Bash** → Standard, reliable, scripting powerhouse
- **Fish** → Beginner-friendly, colorful, interactive
- **Zsh** → Advanced, customizable, modern

👉 Select based on your **workflow needs**: scripting, customization, or ease of use.