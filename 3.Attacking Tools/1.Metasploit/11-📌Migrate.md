## 🧩 What is Migrate and What Does It Provide?

- **Definition:** Changing which process Meterpreter runs inside.
    
- **Why?**
    
    - The initial process may be low-privilege or unstable.
    - If that process terminates, the session dies too.
    - Migrating into a SYSTEM process makes the session stronger and more stable.
- **Benefits:**
    
    - **Stability:** Moving into a long-lived process prevents session drops.
    - **Privilege:** Migrating into a SYSTEM process enables commands like `hashdump`, `kiwi`.
    - **Access:** SYSTEM-level processes allow access to SAM database, LSASS memory, etc.
- **Which processes to migrate into?**
    
    - `lsass.exe` → SYSTEM-level, ideal for credential dumping.
    - `services.exe` → SYSTEM-level, stable.
    - `winlogon.exe` → SYSTEM-level, sometimes protected.
    - `explorer.exe` → User session, useful for GUI-related tasks.
    - General rule: **Pick a SYSTEM-level, long-running process.**

---
## 🎯 Summary

- **Shell** = bare command line, limited control.
- **Meterpreter** = full-featured attacker toolkit, essential for post-exploitation.
- **Transition process:** exploit → shell → background → upgrade/post module → Meterpreter → migrate.
- **Migrate:** moves the session into a stronger, privileged process, granting SYSTEM rights and critical access.
