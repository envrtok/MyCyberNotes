## 🔐 Level Goal

The password for the next level is stored in the file **data.txt**, which contains base64 encoded data

---

## 🛠️ Solution

```powershell
cat data.txt | base64 -d
dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```