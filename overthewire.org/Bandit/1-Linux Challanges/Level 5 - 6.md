## 🔐 Level Goal

The password for the next level is stored in a file somewhere under the **inhere** directory and has all of the following properties:

- human-readable
- 1033 bytes in size
- not executable

---

## 🛠️ Solution

```powershell
#there is a folder called inhere
cd inhere
ls #we saw 10 files
ls * #lists all documents in files
#there is too much files so we cannot try one by one
grep -R . * #this command reads all files
#and we saw the password at maybehere07/.file2
exit
ssh bandit6@bandit.labs.overthewire.org -p 2220
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```