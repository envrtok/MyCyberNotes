## 🔐 Level Goal

The password for the next level is stored **somewhere on the server** and has all of the following properties:

- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

---

## 🛠️ Solution

```powershell
# we should search the file on all the server. so we should enter that
find / -size 33c -user bandit7 -group bandit6  2>/dev/null
	# / means that search on the all server
	# -size 33c means size is 33 byte
	# -user bandit7 means user is bandit7
	# -group bandit6 means group is bandit6
	# 2>/dev/null blocks unnecessary outputs
# and we've found the path
cat /var/lib/dpkg/info/bandit7.password
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```