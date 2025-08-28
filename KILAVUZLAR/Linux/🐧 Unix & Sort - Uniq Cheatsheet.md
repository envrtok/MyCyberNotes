## 📂 1. Dosya Okuma / Görüntüleme

```bash
cat file.txt              # Dosyayı ekrana yazdır
less file.txt             # Kaydırarak görüntüle
more file.txt             # Alternatif kaydırmalı görüntüleme
head -n 10 file.txt       # İlk 10 satır
tail -n 10 file.txt       # Son 10 satır
tail -f file.log          # Log takibi (live)
```

---

## 🔢 2. Satır Sayısı / Kelime / Karakter

```bash
wc file.txt               # Satır, kelime, karakter sayısı
wc -l file.txt            # Satır sayısı
wc -w file.txt            # Kelime sayısı
wc -c file.txt            # Byte sayısı
```

---

## 🌀 3. Sıralama (`sort`)

```bash
sort file.txt                   # Alfabetik sırala
sort -r file.txt                # Ters alfabetik
sort -n file.txt                # Sayısal sırala
sort -nr file.txt               # Sayısal + ters
sort -u file.txt                # Tekil satırlar
sort -k 2 file.txt              # 2. sütuna göre sırala
sort -t ":" -k 3 file.txt       # : ayırıcı, 3. sütuna göre
```

---

## 🔹 4. Tekrarlayan / Tek Geçen Satırlar (`uniq`)

```bash
uniq file.txt                   # Tekrarlayanları sil (sıralı olmalı)
sort file.txt | uniq             # Sıralama + tekrarları temizle
sort file.txt | uniq -c          # Satır başına tekrar sayısı
sort file.txt | uniq -d          # Sadece birden fazla geçen satırlar
sort file.txt | uniq -u          # Sadece tek geçen satırlar
```

---

## ⚡ 5. Pipe & Kombinasyon Örnekleri

```bash
cat file.txt | sort | uniq -c | sort -nr   # En çok tekrar eden satırları sırala
grep "error" logfile | sort | uniq -c      # Logta hata tekrar sayısı
cat users.txt | cut -d: -f1 | sort | uniq  # Kullanıcı adlarını listele
```

---

## 🔑 6. Metin İşleme / Filtreleme

```bash
grep "pattern" file.txt             # Kelime veya regex ara
grep -v "pattern" file.txt          # Hariç tut
cut -d ":" -f1 /etc/passwd          # Sütun seç
awk '{print $2}' file.txt            # 2. sütunu yazdır
tr '[:lower:]' '[:upper:]' < file.txt # Küçük -> büyük harf
head -n 5 file.txt                   # İlk 5 satır
tail -n 5 file.txt                   # Son 5 satır
```

---

## 🐚 7. Dosya / Klasör İşlemleri

```bash
ls -l                               # Detaylı liste
ls -a                               # Gizli dosyalar dahil
cp file1 file2                       # Dosya kopyala
mv file1 file2                       # Dosya taşı / yeniden adlandır
rm file                              # Dosya sil
mkdir folder                          # Klasör oluştur
rmdir folder                          # Boş klasör sil
```

---

## 📊 8. CTF / Pratik Veri İşleme Örnekleri

```bash
sort big.log | uniq -c | sort -nr       # Logta en sık tekrar eden satırlar
cat passwords.txt | sort | uniq -u      # Tek geçen şifreleri bul
grep "FLAG" * | sort | uniq             # Flag içeren dosyaları listele
cut -d: -f1 /etc/passwd | sort | uniq   # Tekil kullanıcı adları
awk '{print $1}' file.txt | sort | uniq -c | sort -nr  # En çok geçen ilk sütun
```

---

💡 **Özet Mantık**

- **`sort`** → Sıralama (alfabetik, sayısal, ters)
    
- **`uniq`** → Tekrarlayan satırları bulma/temizleme
    
- **Pipe** → `sort | uniq`, `grep | sort | uniq -c` gibi kombinasyonlar veri analizi için kritik
    
- **cut/awk/tr/head/tail** → metin parçalama ve ön filtreleme
    

---

İstersen bunu da **CTF / günlük kullanım odaklı tek taş gibi .md cheatsheet** hâline getirip sana verebilirim; böylece `find + cat + grep + sort/uniq` hepsi tek dosyada hazır olur.

Bunu hazırlayayım mı?