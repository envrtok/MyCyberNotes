## **What is SCP?** 🤔
SCP allows copying documents between current machine and remote machine (which is controlling with ssh). It uses SSH encryption for secure file transfer! 🛡️

## **Copying TO Remote Machine** ⬆️
```bash
scp file.txt <username>@<ip-address>:/path
```
- That copys to remote machine 📤➡️🖥️

## **Copying FROM Remote Machine** ⬇️
```bash
scp >username>@<ip-address>:/path file.txt
```
- That copys from machine 🖥️➡️📤

## **Copy Entire Folder**
```bash
scp -r myfolder/ username@ipaddress:/home/username/
```
- Recursively copies folders and all contents 📁🔄

## **Custom Port Connection**
```bash
scp -P 2222 file.txt username@ipaddress:/path
```
- Connects to SSH on port 2222 🚪

## **Preserve File Attributes**
```bash
scp -p file.txt username@ipaddress:/path
```
- Keeps original file timestamps and permissions ⏰

---

## **💡 Pro Tips** 
- SCP uses the same authentication as SSH (passwords or keys)! 🔑
- Use `scp -v` for verbose output to see what's happening! 👀
- Combine with wildcards: `scp *.txt username@ipaddress:/path` 📄
- Perfect for transferring configuration files, backups, or website content! 🚀

Great for quick, secure file transfers between machines! 🔄✨