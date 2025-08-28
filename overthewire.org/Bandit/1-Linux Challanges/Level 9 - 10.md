## 🔐 Level Goal

The password for the next level is stored in the file **data.txt** in one of the few human-readable strings, preceded by several ‘=’ characters.

---

## 🛠️ Solution

```powershell
strings data.txt | grep "=="
FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```