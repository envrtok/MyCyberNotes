## 🔐 Level Goal

The password for the next level is stored in **/etc/bandit_pass/bandit14 and can only be read by user bandit14**. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. **Note:** **localhost** is a hostname that refers to the machine you are working on

---

## 🛠️ Solution

```powershell
ls # we can see the ssh key for loggining level 14. so we can download it to our own computer
exit
scp -P 2220 bandit13@bandit.labs.overthewire.org:~/sshkey.private .

```