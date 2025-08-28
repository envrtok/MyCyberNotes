## 🔐 Level Goal

The password for the next level is stored in a file somewhere under the **inhere** directory and has all of the following properties:

- human-readable
- 1033 bytes in size
- not executable

---

## 🛠️ Solution

```powershell
ls
cd inhere
ls
# there are tons of files and folders. (for see all files, enter "ls ./*")
# we should find our target file with filtering.
find ./* -readable ! -executable -size 1033c
# and we find the file path
cat ./maybehere07/.file2 
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG # it is the password
```