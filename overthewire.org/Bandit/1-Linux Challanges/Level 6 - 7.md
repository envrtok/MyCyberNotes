## 🔐 Level Goal

The password for the next level is stored **somewhere on the server** and has all of the following properties:

- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

---

## 🛠️ Solution

```powershell
#now we know that in server there is tons of files so trying to find one by one is impossible
#we should use find with given properties
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
# -type f : specifies that we are looking for a file  
# -user bandit7 : specifies that the owner must be bandit7  
# -group bandit6 : specifies that the group must be bandit6  
# -size 33c : specifies that the size must be 33 bytes  
# 2>/dev/null : suppresses the "permission denied" messages  
# we can use cat on the resulting path to obtain the password 
exit 
ssh bandit7@bandit.labs.overthewire.org -p 2220
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```