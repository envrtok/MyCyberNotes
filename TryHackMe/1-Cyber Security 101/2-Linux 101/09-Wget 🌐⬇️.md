## **What is Wget?** 🤔
Wget allows you download documents from a web server. It's a powerful command-line tool for downloading files from the internet! 💪

## **Basic Usage** 🚀
```bash
wget (option) (URL)
```

## **Common Examples & Options** 📝

### **Basic Download**
```bash
wget example.com/doc.txt
```
- Downloads current URL and saves it to current path 📥

### **Custom Filename**
```bash
wget -O sweet.txt example.com/doc.txt
```
- Downloads current URL and saves it to current path as sweet.txt instead of original name ✂️

### **Resume Download**
```bash
wget -c example.com/doc.txt
```
- Resumes current downloading 🔄

### **Custom Download Path**
```bash
wget -P /home/user/Downloads example.com/doc.txt
```
- Saves the URL to given path 📁

### **Background Download**
```bash
wget -b example.com/doc.txt
```
- Runs in background 🌌

### **Download Entire Website**
```bash
wget --mirror example.com
```
- Downloads a complete website recursively 🕸️

### **Limit Download Speed**
```bash
wget --limit-rate=100k example.com/largefile.zip
```
- Limits download speed to 100 KB/s 🐢

### **Retry on Failure**
```bash
wget -t 5 example.com/unstable-file.txt
```
- Tries downloading 5 times if it fails 🔄

---

### **💡 Pro Tips** 
- Wget continues downloads even if your internet connection drops! 📶
- Use `wget --help` to see all available options! 🆘
- Combine options like `wget -c -b example.com/file.zip` for powerful downloads! 🔗
- Wget can download from FTP servers too! 📡

Perfect for downloading files, backing up websites, or automating downloads! 🤖✨