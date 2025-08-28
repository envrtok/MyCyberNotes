## 📌 Genel Kullanım

```bash
cat [seçenekler] [dosya...]
```

- Bir veya birden fazla dosyanın içeriğini okur, birleştirir ve ekrana basar.
    
- "concatenate" (birleştirmek) kelimesinden gelir.
    

---

## 📂 1. Temel Kullanımlar

```bash
cat file.txt              # Dosyayı ekrana yazdır
cat file1.txt file2.txt   # Dosyaları ardışık yazdır
cat > new.txt             # Klavyeden girilen veriyi dosyaya yaz (CTRL+D ile bitir)
cat file1 > file2         # İçeriği başka dosyaya yönlendir (overwrite)
cat file1 >> file2        # İçeriği başka dosyanın sonuna ekle (append)
```

---

## 🔢 2. Satır Numaraları

```bash
cat -n file.txt           # Tüm satırları numaralandır
cat -b file.txt           # Sadece boş olmayan satırları numaralandır
```

---

## 📜 3. Özel Karakterler & Formatlama

```bash
cat -E file.txt           # Satır sonlarını $ işaretiyle göster
cat -T file.txt           # TAB karakterlerini ^I olarak göster
cat -A file.txt           # Tüm kontrol karakterlerini göster (-vET kombinasyonu)
cat -s file.txt           # Ardışık boş satırları teke indir
```

---

## 📏 4. Büyük Dosyalar & Performans

```bash
cat large.log | head -n 20   # İlk 20 satırı göster
cat large.log | tail -n 50   # Son 50 satırı göster
cat file | less              # Kaydırarak oku (tercih: less/more)
```

---

## 🌀 5. Dosya Birleştirme

```bash
cat part1.txt part2.txt > full.txt   # Parçaları birleştir
cat *.txt > merged.txt               # Tüm txt dosyalarını birleştir
```

---

## 🔒 6. Binary & Özel Dosyalar

```bash
cat file.bin               # Binary dosyayı raw göster
cat image.jpg > copy.jpg   # Dosya kopyalama
cat /dev/urandom | head -c 100 > rand.bin   # 100 byte rastgele veri üret
```

---

## 🐚 7. Standart Akış Kullanımı

```bash
cat                        # stdin’den oku (CTRL+D ile bitir)
echo "hello" | cat -n      # Pipe içeriğini numaralandır
cat - < file.txt           # stdin + dosya birleştir
```

---

## ⚙️ 8. Kullanışlı Hileler

```bash
cat -vet file.txt          # Görünmez karakterleri göster
cat file | wc -l           # Satır sayısı öğren
cat file | sort | uniq     # Satırları sırala + tekrarları temizle
```

---

## 🎯 9. CTF / Güvenlik Senaryoları

```bash
cat file.txt               # Klasik flag dosyası açma
cat file*name.txt         # Boşluk içeren dosya okuma
cat "./-flag.txt"          # Tire ile başlayan dosya okuma
cat $(ls -a | grep flag)   # Gizli dosya okuma
cat file.txt | base64 -d   # Base64 çözme
cat file.txt | xxd         # Hex dump alma
cat file.txt | strings     # Binary içinden yazı ayıklama
cat /dev/null > file.txt   # Dosyayı hızlıca boşalt
```

---

## 🧩 10. Alternatifler (daha büyük işler için)

- `less` → Büyük dosyaları kaydırarak okumak için.
    
- `head` / `tail` → İlk/son satırları görmek için.
    
- `xxd`, `hexdump`, `strings` → Binary dosyaları analiz etmek için.
    

---

✅ Bu kılavuz günlük kullanım + CTF + dosya manipülasyonu için **tam kapsamlı**.  
💡 `cat` çoğu zaman basit görünür ama garip dosya adları, binary içerikler, pipe kombinasyonlarıyla CTF’te çok kritik hale gelir.

---