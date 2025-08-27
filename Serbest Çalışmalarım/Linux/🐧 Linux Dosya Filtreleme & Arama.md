

## 1️⃣ Dosya ve dizin arama

### `find`

```bash
# Belirli bir dosya adı ara
find /path -name "dosya.txt"

# Büyük/küçük harf duyarsız ara
find /path -iname "dosya.txt"

# Belirli bir uzantıya sahip dosyalar
find /path -type f -name "*.log"

# Son değiştirilme tarihine göre ara (son 1 gün)
find /path -type f -mtime -1

# 1MB’dan büyük dosyalar
find /path -type f -size +1M

# Belirli izinlere sahip dosyalar (644)
find /path -type f -perm 644

# Symbolic linkleri bul
find /path -type l
```

## 2️⃣ İçerik arama

### `grep`

```bash
# Dosyada belirli bir kelimeyi ara
grep "anahtar" dosya.txt

# Alt dizinlerde ara
grep -r "anahtar" /path

# Satır numarası ile göster
grep -n "anahtar" dosya.txt

# Büyük/küçük harf duyarsız
grep -i "anahtar" dosya.txt

# Belirli uzantılarda ara
grep "anahtar" *.log

# Kelime eşleşmesini tam yap
grep -w "anahtar" dosya.txt

# Regex ile örnek
grep -E "user[0-9]+" dosya.txt
```

## 3️⃣ Satır filtreleme & sıralama

### `sort` & `uniq`

```bash
# Dosyayı alfabetik sırala
sort dosya.txt

# Ters sırada
sort -r dosya.txt

# Tekrarlayan satırları filtrele
uniq dosya.txt

# Sıralı ve tekrarsız
sort dosya.txt | uniq
```

### `head` & `tail`

```bash
# İlk 10 satır
head dosya.txt

# Son 10 satır
tail dosya.txt

# Sonu takip et (log izleme)
tail -f /var/log/syslog
```

## 4️⃣ Dosya içerik parçalama

### `cut`

```bash
# Virgülle ayrılmış dosyada 2. sütunu al
cut -d',' -f2 dosya.csv

# Taban çizgi ile ayrılmış
cut -d'_' -f1 dosya.txt
```

### `awk`

```bash
# Boşlukla ayrılmış 2. sütunu al
awk '{print $2}' dosya.txt

# Belirli koşula göre filtrele
awk '$3 > 100 {print $1,$3}' dosya.txt
```

## 5️⃣ Zincirleme (pipe) örnekleri

```bash
# log dosyasında "error" geçen satırları bul, sırala, tekrarsız yap
grep "error" *.log | sort | uniq

# belirli uzantıdaki dosyalarda "root" kelimesi arayıp satır numarasıyla göster
find / -type f -name "*.conf" 2>/dev/null | xargs grep -n "root"

# büyük log dosyasında sadece ilk 50 unique error
grep "error" big.log | sort | uniq | head -n 50
```

## 6️⃣ Faydalı ipuçları

- `2>/dev/null` → izin reddi ve hataları gizler
    
- `xargs` → `find` çıktısını başka komutla işlemek için
    
- Regex kullanımı (`grep -E`) → daha karmaşık filtreler için
    
- Symbolic link ve izinler → root erişimi gerektiren dosyalarda dikkat
    

💡 **Özet:**

- `find` → dosya/dizin bazlı arama
    
- `grep` → içerik arama
    
- `awk` & `cut` → sütun/alan bazlı filtreleme
    
- `sort` & `uniq` → sıralama ve tekrarlardan kurtulma
    
- `pipe (|)` → komutları zincirleme