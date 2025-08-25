## 🔐 Level Goal

The password for the next level is stored in the file **data.txt** and is the only line of text that occurs only once

---

## 🛠️ Solution

```powershell
# for finding non repeating line we use that
sort data.txt | uniq -u
# and we got the password
exit
ssh bandit9@bandit.labs.overthewire.org -p 2220
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```