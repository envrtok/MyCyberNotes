## 🔐 Level Goal

The password for the next level is stored in the only human-readable file in the **inhere** directory. Tip: if your terminal is messed up, try the “reset” command.

---

## 🛠️ Solution

```powershell
#there is a folder called inhere
cd inhere
ls #we saw 10 files
cat -file00
cat ./-file00 #reading tryings were unsuccessfull
cat -- -file00 #now we could read, but password is not here
cat -- -file07 #we got the password
exit
ssh bandit5@bandit.labs.overthewire.org -p 2220
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```