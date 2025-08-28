## 📌 Genel Kullanım

```bash
grep [seçenekler] [pattern] [dosya...]
```

- `pattern` → aranan kelime veya regex
    
- `dosya` → taranacak dosya veya dizin
    
- Varsayılan: eşleşen satırı ekrana yazdırır
    

---

## 📂 1. Temel Kullanım

```bash
grep "hello" file.txt         # Kelimeyi dosyada ara
grep "hello" file1 file2      # Birden fazla dosyada ara
grep -i "hello" file.txt      # Büyük/küçük harf duyarsız
grep -v "skip" file.txt       # Belirtilen kelimeyi hariç tut
```

---

## 🔢 2. Satır Numaraları & Konum

```bash
grep -n "hello" file.txt      # Satır numarası ile göster
grep -c "hello" file.txt      # Kaç kez geçtiğini say
grep -H "hello" file.txt      # Dosya adını yazdır
grep -l "hello" *.txt         # Sadece dosya adlarını göster
grep -L "hello" *.txt         # Kelimeyi içermeyen dosyalar
```

---

## 🌀 3. Recursive & Pipe Kullanımı

```bash
grep -r "password" /etc       # Klasörde recursive ara
grep -Ri "password" /etc      # Recursive + ignore case
grep "flag" file.txt | less   # Uzun çıktıyı kaydır
cat file.txt | grep "hello"   # Pipe ile ara
```

---

## 📜 4. Regex & Pattern

```bash
grep "^Start" file.txt        # Satır başı ile eşleşme
grep "End$" file.txt          # Satır sonu ile eşleşme
grep "[0-9]" file.txt         # Rakam içeriyorsa
grep -E "foo|bar" file.txt    # Extended regex (OR)
grep -o "pattern" file.txt    # Sadece eşleşen kısmı yazdır
grep -P "\d{3}-\d{2}-\d{4}" file.txt  # Perl regex
```

---

## 🔑 5. Renk & Vurgulama

```bash
grep --color=auto "pattern" file.txt  # Eşleşeni renklendir
grep --color=always "pattern" file.txt
```

---

## ⚡ 6. Büyük Dosyalar / Performans

```bash
grep -r --exclude-dir="node_modules" "TODO" /project
grep -r --include="*.py" "TODO" /project
grep -ri --exclude="*.log" "error" /var/log
```

---

## 🐚 7. CTF ve Güvenlik Senaryoları

```bash
grep -ril "flag" /              # Flag içeren dosyaları bul
grep -ril "password" /etc/      # Şifre içeren dosyaları bul
grep -r "ssh" /home/            # SSH ile ilgili satırlar
grep -Ero "[A-Za-z0-9]{32}" .  # MD5/flag pattern eşleşmeleri
grep -P "FLAG\{.*?\}" .         # Flag pattern regex
grep -n "root:" /etc/passwd     # Şifre/ID kontrol
```

---

## 🧩 8. Pipe ile Kombinasyonlar

```bash
find / -type f -name "*.txt" 2>/dev/null | xargs grep -i "flag"
cat file.txt | grep -v "DEBUG" | grep "ERROR"
dmesg | grep -i "usb"
journalctl | grep -i "failed"
strings data.txt | grep "^==="        # Satır başı === ile başlayan human-readable satırlar
strings data.txt | grep "^===" | head -n 1  # İlk eşleşmeyi al
cat data.txt | strings | grep "^==="     # Alternatif pipe kombinasyonu
find / -type f -exec strings {} \; | grep "FLAG"  # Sistemde flag içeren human-readable stringler
```

---

## 🔹 Kurallar Özet

- **Dosya içeriği aramak için `grep`**
    
- **Dosya adı / izin / boyut aramak için `find`**
    
- **CTF senaryolarında genelde ikisi birlikte**
    
- Regex, ignore-case, recursive ve pipe kombinasyonları kritik
    
---