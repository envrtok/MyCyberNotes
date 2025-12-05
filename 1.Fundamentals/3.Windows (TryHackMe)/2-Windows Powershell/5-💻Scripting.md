#### **1. What is Scripting? 📜**
*   **Definition:** Writing a series of commands in a text file (a **script**) to automate tasks.
*   **Analogy:** Giving a computer a **"to-do list"** it can execute automatically.
*   **Benefits:** Saves time ⏱️, reduces errors ❌, and handles complex tasks.

#### **2. PowerShell Scripting in Cyber Security 🛡️**
*   A **crucial skill** for all cyber security roles.

*   **Blue Team 🔵 (Defense):**
    *   **Log analysis** and **anomaly detection**
    *   **Malware reverse-engineering**
    *   **Scanning for Indicators of Compromise (IOCs)**

*   **Red Team 🔴 (Offense):**
    *   **System enumeration**
    *   **Executing remote commands**
    *   **Bypassing defenses** with obfuscated scripts

*   **System Administrators ⚙️:**
    *   **Automate integrity checks**
    *   **Enforce security policies**
    *   **Monitor system health** and **respond to incidents**

#### **3. The Powerful `Invoke-Command` Cmdlet 🚀**
*   **Purpose:** Executes commands on **remote systems**.

*   **Example 1: Run a Script Remotely**
    ```powershell
    Invoke-Command -FilePath c:\scripts\test.ps1 -ComputerName Server01
    ```

*   **Example 2: Run a Single Command Remotely**
    ```powershell
    Invoke-Command -ComputerName Server01 -Credential Domain01\User01 -ScriptBlock { Get-Culture }
    ```
    *   `-ScriptBlock` lets you run any command as if you were on the remote computer.

#### **4. Key Takeaway 🎯**
*   PowerShell scripting is an **essential capability** in the cyber security toolkit, whether used for **defense** or **offense**.