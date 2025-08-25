## 🔐 Level Goal

The password for the next level is stored in a file called --spaces in this filename-- located in the home directory

---

## 🛠️ Solution

```powershell
ls #we saw the file called "--spaces in this filename-- 
cat ./--spaces in this filename-- #reading trying was unsuccessfull
#file has spaces in filename, so we should put * into blanks 
cat ./--spaces*in*this*filename-- #and finally we got the password
exit
ssh bandit3@bandit.labs.overthewire.org -p 2220
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```