## 🔐 Level Goal

The password for the next level is stored in the file **data.txt** next to the word **millionth**

---

## 🛠️ Solution

```powershell
# for finding a word in a file we use grep
grep millionth data.txt
# and we got the password
exit
ssh bandit8@bandit.labs.overthewire.org -p 2220
dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```