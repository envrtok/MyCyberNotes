## 🔐 Level Goal

The password for the next level is stored in the file **data.txt** in one of the few human-readable strings, preceded by several ‘=’ characters.

---

## 🛠️ Solution

```powershell
cat data.txt
# we need to get string characters first, then we should filter for staring with =
strings data.txt | grep ^=
# and we got the password
exit
ssh bandit10@bandit.labs.overthewire.org -p 2220
FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```