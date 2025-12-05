### 🧩 Processes

- `Get-Process` → gives currently running processes

```powershell
PS C:\> Get-Process
```

---

### ⚙️ Services

- `Get-Service` → gives services and statuses of all services

```powershell
PS C:\> Get-Service
```

---

### 🌐 TCP Connections

- `Get-NetTCPConnection` → displays currently active TCP connections

```powershell
PS C:\> Get-NetTCPConnection
```

---

### 🔐 File Hashing

- `Get-FileHash -Path <path>` → gets hashes for the given path

```powershell
PS C:\> Get-FileHash -Path "C:\Users\user\example.txt"
```