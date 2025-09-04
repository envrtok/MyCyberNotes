## 🔹 1. Temel

```bash
gobuster -h                        # Yardım
gobuster <mode> -u URL -w wordlist # Genel kullanım
```

Modlar:

- `dir` → Dizin & dosya brute force
    
- `dns` → Subdomain brute force
    
- `vhost` → Virtual host brute force
    
- `s3` → AWS S3 bucket arama
    
- `fuzz` → Fuzzing (parametre/dosya adı vs.)
    

---

## 🔹 2. Dizin / Dosya Tarama (dir mode)

```bash
gobuster dir -u http://<ip>/ -w wordlist.txt
gobuster dir -u http://<ip>/ -w wordlist.txt -x php,html,txt    # Uzantı denemesi
gobuster dir -u http://<ip>/ -w wordlist.txt -t 50              # Thread sayısı
gobuster dir -u http://<ip>/ -w wordlist.txt -q                 # Sessiz mod
gobuster dir -u http://<ip>/ -w wordlist.txt -s 200,204,301,302 # Belirli status kodları
gobuster dir -u http://<ip>/ -w wordlist.txt -b 404             # 404 hariç göster
gobuster dir -u http://<ip>/ -w wordlist.txt -e                 # Tam URL göster
```

---

## 🔹 3. Sanal Host (vhost mode)

```bash
gobuster vhost -u http://<ip>/ -w subdomains.txt
gobuster vhost -u http://site.com -w vhosts.txt -t 50
```

👉 CTF’de sık kullanılan, özellikle `Host` header bruteforce için.

---

## 🔹 4. DNS / Subdomain (dns mode)

```bash
gobuster dns -d site.com -w subdomains.txt
gobuster dns -d site.com -w subdomains.txt -i         # IP adresini de göster
gobuster dns -d site.com -w subdomains.txt -r 8.8.8.8 # Özel DNS resolver
```

---

## 🔹 5. AWS S3 Bucket (s3 mode)

```bash
gobuster s3 -w s3-buckets.txt
```

👉 Çoğu CTF’de çıkmaz ama cloud temalı olanlarda işine yarayabilir.

---

## 🔹 6. Fuzzing (fuzz mode)

```bash
gobuster fuzz -u "http://<ip>/FUZZ" -w words.txt
gobuster fuzz -u "http://<ip>/page.php?FUZZ=1" -w params.txt
```

👉 Parametre, endpoint veya dosya ismi fuzzing için.

---

## 🔹 7. Faydalı Parametreler

```bash
-u <url>            # Hedef URL
-w <wordlist>       # Wordlist dosyası
-t <threads>        # Thread sayısı (default 10)
-x <exts>           # Uzantılar (php,html,txt)
-s <codes>          # İlgilenilen status kodları
-b <codes>          # Hariç tutulacak kodlar
-o <file>           # Sonuç çıktısı
-q                  # Sessiz mod
-e                  # Tam URL göster
```

---

## 🔹 8. Wordlist Önerileri

- `/usr/share/seclists/Discovery/Web-Content/`
    
- `/usr/share/wordlists/dirb/common.txt`
    
- `raft-large-files.txt`
    
- `raft-large-directories.txt`
    
- `subdomains-top1million-5000.txt`
    

---

## 🔹 9. CTF Workflow – Strateji

### 🟢 1. Hızlı keşif

```bash
gobuster dir -u http://<ip>/ -w common.txt -q -t 50
```

👉 Hedefte en bilinen dizin/dosyaları hızlıca bul.

### 🟢 2. Uzantılar ekle

```bash
gobuster dir -u http://<ip>/ -w common.txt -x php,html,txt
```

👉 Özellikle webshell/flag saklama için `.php` ve `.txt` kritik.

### 🟢 3. Geniş wordlist denemesi

```bash
gobuster dir -u http://<ip>/ -w directory-list-2.3-medium.txt -t 50
```

👉 İlk taramada çıkmayan endpoint’leri yakalayabilirsin.

### 🟢 4. Subdomain / Vhost keşfi

```bash
gobuster vhost -u http://site.com -w vhosts.txt
gobuster dns -d site.com -w subdomains.txt
```

👉 Özellikle CTF’lerde gizli panel veya admin login genelde subdomain’de çıkar.

### 🟢 5. Parametre fuzzing

```bash
gobuster fuzz -u "http://site.com/page.php?FUZZ=1" -w params.txt
```

👉 Gizli GET parametreleri bulup SQLi, RCE gibi açığa gidebilirsin.
