- Windows's default command line interpreter is **`cmd.exe`**
    - 🖥️ **CMD** → legacy, text-based executor _(like a basic calculator)_
    - 🔧 **PowerShell** → modern automation & scripting environment _(like a programming language with math library)_

---

## 📋 Basic System Information

### 🧹 Clear Screen

- `"cls"` clears all page

---

### ❓ Help Command

- `"help <something>"` provides information for a command
```cmd
user@WINSRV2022-CORE C:\Users\user>help cls
Clears the screen.

CLS
```

---

### 🏷️ Version Info (`ver`)

- `"ver"` command gives OS version

```cmd
user@WINSRV2022-CORE C:\Users\user>ver
Microsoft Windows [Version 10.0.20348.2655]
```

---

### 🖥️ System Information (`systeminfo`)

- `"systeminfo"` gives various information about OS, system details, processor and memory

```cmd
user@WINSRV2022-CORE C:\Users\user>systeminfo

Host Name:                 WINSRV2022-CORE
OS Name:                   Microsoft Windows Server 2022 Datacenter
OS Version:                10.0.20348 N/A Build 20348
OS Manufacturer:           Microsoft Corporation
OS Configuration:          Standalone Server
OS Build Type:             Multiprocessor Free
Registered Owner:          Windows User
Registered Organization:
Product ID:                00454-60000-00001-AA763
Original Install Date:     4/23/2024, 7:36:29 PM
System Boot Time:          11/17/2025, 1:19:48 PM
System Manufacturer:       Amazon EC2
System Model:              t3a.small
System Type:               x64-based PC
Processor(s):              1 Processor(s) Installed.
                           [01]: AMD64 Family 23 Model 1 Stepping 2 AuthenticAMD ~2200 Mhz
BIOS Version:              Amazon EC2 1.0, 10/16/2017
Windows Directory:         C:\Windows
System Directory:          C:\Windows\system32
Boot Device:               \Device\HarddiskVolume1
System Locale:             en-us;English (United States)
Input Locale:              en-us;English (United States)
Time Zone:                 (UTC+00:00) Dublin, Edinburgh, Lisbon, London
Total Physical Memory:     1,996 MB
Available Physical Memory: 1,187 MB
Virtual Memory: Max Size:  2,380 MB
Virtual Memory: Available: 1,606 MB
Virtual Memory: In Use:    774 MB
Page File Location(s):     C:\pagefile.sys
Domain:                    WORKGROUP
Logon Server:              N/A
Hotfix(s):                 3 Hotfix(s) Installed.
                           [01]: KB5041948
                           [02]: KB5041160
                           [03]: KB5041590
Network Card(s):           1 NIC(s) Installed.
                           [01]: Amazon Elastic Network Adapter
                                 Connection Name: Ethernet
                                 DHCP Enabled:    Yes
                                 DHCP Server:     10.10.0.1
                                 IP address(es)
                                 [01]: 10.10.138.170
                                 [02]: fe80::9e5:86c4:4159:c64a
Hyper-V Requirements:      A hypervisor has been detected. Features required for Hyper-V will not be displayed.
```

---

### 📂 Environment Variables (`set`)

- `"set"` command gives where Windows executes commands as paths

```cmd
user@WINSRV2022-CORE C:\Users\user>set
ALLUSERSPROFILE=C:\ProgramData
APPDATA=C:\Users\user\AppData\Roaming
ChocolateyInstall=C:\ProgramData\chocolatey
CommonProgramFiles=C:\Program Files\Common Files
CommonProgramFiles(x86)=C:\Program Files (x86)\Common Files
CommonProgramW6432=C:\Program Files\Common Files
COMPUTERNAME=WINSRV2022-CORE
ComSpec=C:\Windows\system32\cmd.exe
DriverData=C:\Windows\System32\Drivers\DriverData
EC2LAUNCH_TELEMETRY=1
HOME=C:\Users\user
HOMEDRIVE=C:
HOMEPATH=\Users\user
LOCALAPPDATA=C:\Users\user\AppData\Local
LOGNAME=user
NUMBER_OF_PROCESSORS=2
OS=Windows_NT
Path=C:\Windows\system32;C:\Windows;C:\Windows\System32\Wbem;C:\Windows\System32\WindowsPowerShell\v1.0\;C:\Windows\System32\OpenSSH\;C:\ProgramData\chocolatey\bin;C:\Windows\system32\config\systemprofile\AppData\Local\Microsoft\WindowsApps;C:\Users\user\AppData\Local\Microsoft\WindowsApps;
PATHEXT=.COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC
PROCESSOR_ARCHITECTURE=AMD64
PROCESSOR_IDENTIFIER=AMD64 Family 23 Model 1 Stepping 2, AuthenticAMD
PROCESSOR_LEVEL=23
PROCESSOR_REVISION=0102
ProgramData=C:\ProgramData
ProgramFiles=C:\Program Files
ProgramFiles(x86)=C:\Program Files (x86)
ProgramW6432=C:\Program Files
PROMPT=user@WINSRV2022-CORE $P$G
PSModulePath=C:\Program Files\WindowsPowerShell\Modules;C:\Windows\system32\WindowsPowerShell\v1.0\Modules
PUBLIC=C:\Users\Public
SHELL=c:\windows\system32\cmd.exe
SSH_CLIENT=10.10.72.136 56568 22
SSH_CONNECTION=10.10.72.136 56568 10.10.208.79 22
SSH_TTY=windows-pty
SystemDrive=C:
SystemRoot=C:\Windows
TEMP=C:\Users\user\AppData\Local\Temp
TERM=xterm-256color
TMP=C:\Users\user\AppData\Local\Temp
USER=user
USERDOMAIN=WORKGROUP
USERNAME=user
USERPROFILE=C:\Users\user
windir=C:\Windows
```

---