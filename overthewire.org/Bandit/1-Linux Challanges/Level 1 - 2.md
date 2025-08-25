## 🔐 Level Goal

The password for the next level is stored in a file called **-** located in the home directory

---

## 🛠️ Solution

```powershell
ls #we saw "-" file
cat - #we tried to read file but it was unsuccessfull
cat ./- #and finally we got the password for level 2
exit
ssh bandit2@bandit.labs.overthewire.org -p 2220
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```