## 🔐 Level Goal

The password for the next level is stored in a hidden file in the **inhere** directory.

---

## 🛠️ Solution

```powershell
#there is a folder called inhere
cd inhere
ls #nothing we can see
ls -a #we saw the file called ..Hiding-From-You
cat ..Hiding-From-You #and we got the password
exit
ssh bandit4@bandit.labs.overthewire.org -p 2220
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```