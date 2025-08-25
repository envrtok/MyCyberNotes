## 🔐 Level Goal

The password for the next level is stored in a file called **readme** located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

---

## 🛠️ Solution

```powershell
cat readme #we learned password of bandit1
exit #we logged out from bandit1
ssh bandit1@bandit.labs.overthewire.org -p 2220
#when asked for password
ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```