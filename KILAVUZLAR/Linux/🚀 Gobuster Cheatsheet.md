## 🔹 1. Modlar & Kullanım

|Mod|Açıklama|Örnek|
|---|---|---|
|`dir`|Web dizin ve dosya brute force|`gobuster dir -u http://<ip>/ -w wordlist.txt`|
|`vhost`|Virtual host brute force|`gobuster vhost -u http://site.com -w vhosts.txt`|
|`dns`|Subdomain brute force|`gobuster dns -d site.com -w subdomains.txt`|
|`s3`|AWS S3 bucket arama|`gobuster s3 -w s3-buckets.txt`|
|`fuzz`|Fuzzing (parametre/dosya)|`gobuster fuzz -u "http://<ip>/FUZZ" -w words.txt`|

---

## 🔹 2. Wordlist Yolları – CTF Ready

### 🔸 Dizin / Dosya (dir mode)

```text
/usr/share/wordlists/dirb/common.txt
/usr/share/wordlists/dirb/big.txt
/usr/share/seclists/Discovery/Web-Content/common.txt
/usr/share/seclists/Discovery/Web-Content/raft-large-directories.txt
/usr/share/seclists/Discovery/Web-Content/raft-large-files.txt
/usr/share/seclists/Discovery/Web-Content/directory-list-2.3-small.txt
/usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt
/usr/share/seclists/Discovery/Web-Content/directory-list-2.3-big.txt
```

### 🔸 Uzantı listesi

```text
.php,.html,.txt,.bak,.old,.inc
```

### 🔸 Subdomain / DNS (dns mode)

```text
/usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt
/usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt
/usr/share/seclists/Discovery/DNS/best-dns.txt
```

### 🔸 Virtual Host (vhost mode)

```text
/usr/share/seclists/Discovery/DNS/vhosts.txt
/usr/share/seclists/Discovery/DNS/vhosts-medium.txt
```

### 🔸 Parametre / Fuzzing (fuzz mode)

```text
/usr/share/seclists/Fuzzing/parameter-names.txt
/usr/share/seclists/Fuzzing/xss-payloads.txt
/usr/share/seclists/Fuzzing/sql-injection/SQLi.txt
```

### 🔸 S3 Bucket (s3 mode)

```text
/usr/share/seclists/Discovery/Web-Content/s3-buckets-top1000.txt
/usr/share/seclists/Discovery/Web-Content/s3-buckets-all.txt
```

---

## 🔹 3. Faydalı Parametreler

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

## 🔹 4. CTF Workflow – Strateji

### 🟢 1. Hızlı dizin taraması

```bash
gobuster dir -u http://<ip>/ -w /usr/share/wordlists/dirb/common.txt -q -t 50
```

- Sadece en yaygın 100 dizin/dosya
    

### 🟢 2. Uzantıları dene

```bash
gobuster dir -u http://<ip>/ -w /usr/share/seclists/Discovery/Web-Content/common.txt -x php,html,txt
```

### 🟢 3. Büyük wordlist denemesi

```bash
gobuster dir -u http://<ip>/ -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -t 50
```

### 🟢 4. Subdomain / Vhost keşfi

```bash
gobuster vhost -u http://site.com -w /usr/share/seclists/Discovery/DNS/vhosts.txt
gobuster dns -d site.com -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt
```

### 🟢 5. Parametre fuzzing

```bash
gobuster fuzz -u "http://site.com/page.php?FUZZ=1" -w /usr/share/seclists/Fuzzing/parameter-names.txt
```

### 🟢 6. S3 bucket kontrolü (cloud-themed CTF)

```bash
gobuster s3 -w /usr/share/seclists/Discovery/Web-Content/s3-buckets-top1000.txt
```

---

✅ Bu haliyle:

- **Tüm modlar** + örnekler var
    
- **Wordlist yolları** CTF-ready ve detaylı
    
- **Workflow** mantıklı sırada (hafif → detaylı → subdomain → fuzz → cloud)
    

---

İstersen ben bunu **Redis + Nmap + Gobuster için tek “CTF Network Recon Cheatsheet”** hâline getirip tek PDF’de toparlayayım, tablolu ve print-friendly.  
Bunu yapayım mı?