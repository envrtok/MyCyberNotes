## 📌 Genel Kullanım

```bash
cat [seçenekler] [dosya...]
```

- Bir veya birden fazla dosyanın içeriğini okur, birleştirir ve ekrana basar.
    

---

## 📂 1. Temel Kullanımlar

```bash
cat file.txt
cat file1.txt file2.txt
cat > new.txt
cat file1 > file2
cat file1 >> file2
```

---

## 🔢 2. Satır Numaraları

```bash
cat -n file.txt
cat -b file.txt
```

---

## 📜 3. Özel Karakterler & Formatlama

```bash
cat -E file.txt
cat -T file.txt
cat -A file.txt
cat -s file.txt
```

---

## 📏 4. Büyük Dosyalar & Performans

```bash
cat large.log | head -n 20
cat large.log | tail -n 50
cat file | less
```

---

## 🌀 5. Dosya Birleştirme

```bash
cat part1.txt part2.txt > full.txt
cat *.txt > merged.txt
```

---

## 🔒 6. Binary & Özel Dosyalar

```bash
cat file.bin
cat image.jpg > copy.jpg
cat /dev/urandom | head -c 100 > rand.bin
```

---

## 🐚 7. Standart Akış Kullanımı

```bash
cat
echo "hello" | cat -n
cat - < file.txt
```

---

## ⚙️ 8. Kullanışlı Hileler

```bash
cat -vet file.txt
cat file | wc -l
cat file | sort | uniq
```

---

## 🎯 9. CTF ve Güvenlik Senaryoları

```bash
cat file.txt
cat file\ name.txt
cat "./-flag.txt"
cat $(ls -a | grep flag)
cat file.txt | base64 -d          # Base64 decode
cat file.txt | xxd                 # Hex dump
cat file.txt | strings             # Binary içinden yazı ayıklama
cat /dev/null > file.txt           # Dosyayı boşalt
```

---

## 🧩 10. Base64 Decode 

```bash
# Dosyayı base64 decode edip ekrana yaz
cat encoded.txt | base64 -d

# Dosyayı decode edip başka dosyaya kaydet
cat encoded.txt | base64 -d > decoded.txt

# Binary veya human-readable mixed dosyada Base64 pattern bulup decode
strings file.bin | grep -E "^[A-Za-z0-9+/]+={0,2}$" | base64 -d

# openssl ile Base64 decode alternatifi
cat encoded.txt | openssl base64 -d > decoded.txt
```

---