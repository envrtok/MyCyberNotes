## 🔐 Level Goal

The password for the next level is stored in **/etc/bandit_pass/bandit14 and can only be read by user bandit14**. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. **Note:** **localhost** is a hostname that refers to the machine you are working on

---

## 🛠️ Solution

```bash
ls # we can see the ssh key for loggining level 14. so we can download it to our own computer
exit
scp -P 2220 bandit13@bandit.labs.overthewire.org:~/sshkey.private .
FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn # password of level 13
# and it has been downloaded successfully
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220 
# and we logged in!
```