## 🚀 TEMEL KULLANIM
```bash
# Temel dizin tarama
gobuster dir -u http://hedefsite.com -w wordlist.txt

# SSL ile tarama
gobuster dir -u https://hedefsite.com -w wordlist.txt

# Belirli uzantılar ile tarama
gobuster dir -u http://hedefsite.com -w wordlist.txt -x php,html,txt
```

## 📁 DİZİN/DOSYA TARAMA (dir)
```bash
# Basit dizin tarama
gobuster dir -u http://10.10.10.10 -w /usr/share/wordlists/dirb/common.txt

# Özel uzantılar ile
gobuster dir -u http://hedef.com -w wordlist.txt -x php,html,js,txt,bak

# Özel header ekleme
gobuster dir -u http://hedef.com -w wordlist.txt -H "Authorization: Bearer token123"

# Thread sayısı belirleme
gobuster dir -u http://hedef.com -w wordlist.txt -t 50

# Zaman aşımı ayarı
gobuster dir -u http://hedef.com -w wordlist.txt --timeout 10s

# Status code filtreleme
gobuster dir -u http://hedef.com -w wordlist.txt -s 200,204,301,302,307,401,403

# Sonuçları dosyaya yazma
gobuster dir -u http://hedef.com -w wordlist.txt -o results.txt

# Proxy kullanma
gobuster dir -u http://hedef.com -w wordlist.txt -p http://proxy:8080

# Özel kullanıcı agent
gobuster dir -u http://hedef.com -w wordlist.txt -a "Mozilla/5.0 Custom"
```

## 🌐 VHOST/VIRTUAL HOST TARAMA (vhost)
```bash
# Vhost tarama
gobuster vhost -u http://hedef.com -w subdomains.txt

# Vhost tarama (base domain ile)
gobuster vhost -u http://hedef.com -w subdomains.txt -b hedef.com

# HTTPS vhost tarama
gobuster vhost -u https://hedef.com -w subdomains.txt
```

## 🔍 DNS TARAMA (dns)
```bash
# DNS subdomain tarama
gobuster dns -d hedef.com -w subdomains.txt

# Özel DNS sunucusu
gobuster dns -d hedef.com -w subdomains.txt -r 8.8.8.8

# Show IP addresses
gobuster dns -d hedef.com -w subdomains.txt -i

# Concurrent threads
gobuster dns -d hedef.com -w subdomains.txt -t 30
```

## 🗂️ S3 BUCKET TARAMA (s3)
```bash
# S3 bucket tarama
gobuster s3 -w bucket-names.txt
```

## ⚙️ GELİŞMİŞ AYARLAR
```bash
# Recursive tarama (dikkatli kullanın!)
gobuster dir -u http://hedef.com -w wordlist.txt -r

# Expanded mode (daha fazla detay)
gobuster dir -u http://hedef.com -w wordlist.txt -e

# No progress gösterme
gobuster dir -u http://hedef.com -w wordlist.txt -q

# Pattern eşleme
gobuster dir -u http://hedef.com -w wordlist.txt -p "/admin/*"

# Cookie ekleme
gobuster dir -u http://hedef.com -w wordlist.txt -c "session=abc123"

# Delay between requests
gobuster dir -u http://hedef.com -w wordlist.txt -d 100ms
```

## 🎯 PRATİK ÖRNEKLER
```bash
# Hızlı tarama
gobuster dir -u http://10.10.10.10 -w /usr/share/wordlists/dirb/common.txt -t 30 -x php,txt,html

# Kapsamlı tarama
gobuster dir -u http://hedef.com -w /usr/share/wordlists/dirb/big.txt -t 50 -x php,html,js,txt,bak,old -s 200,301,302,403 -e

# Subdomain keşfi
gobuster dns -d hedef.com -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt -t 50 -i

# Vhost tarama örneği
gobuster vhost -u https://hedef.com -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt -t 30
```

## 📊 ÇIKTI FORMATLARI
```bash
# JSON çıktı
gobuster dir -u http://hedef.com -w wordlist.txt -o results.json -f json

# Normal çıktı
gobuster dir -u http://hedef.com -w wordlist.txt -o results.txt

# MD format
gobuster dir -u http://hedef.com -w wordlist.txt -o results.md -f md
```

## ⚠️ ÖNEMLİ PARAMETRELER
| Parametre | Açıklama |
|-----------|----------|
| `-u` | Hedef URL |
| `-w` | Wordlist dosyası |
| `-t` | Thread sayısı (default: 10) |
| `-x` | Dosya uzantıları |
| `-s` | Gösterilecek status kodları |
| `-b` | Blacklist status kodları |
| `-e` | Expanded mode |
| `-q` | Quiet mode |
| `-o` | Çıktı dosyası |
| `-f` | Çıktı formatı |

## 🔧 YAYGIN WORDLİSTLER
```bash
/usr/share/wordlists/dirb/common.txt
/usr/share/wordlists/dirb/big.txt
/usr/share/wordlists/dirbuster/directory-list-*.txt
/usr/share/wordlists/SecLists/Discovery/Web-Content/*
/usr/share/wordlists/SecLists/Discovery/DNS/*
```

**Not:** Her zaman etik hacking prensiplerine uyun ve yalnızca sahip olduğunuz sistemlerde test yapın! 🛡️