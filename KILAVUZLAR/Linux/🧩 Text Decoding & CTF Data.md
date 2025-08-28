### 0️⃣ Dosya Türü Kontrolü ve Uzantı Değiştirme

```bash
# Dosya türünü kontrol et
file data.txt
file encoded.gz
file archive.tar.bz2

# Örnek çıktı:
# data.txt: ASCII text
# encoded.gz: gzip compressed data
# archive.tar.bz2: bzip2 compressed data

# Dosya uzantısını değiştirmek (rename)
mv file.old file.new
mv encoded unknown.gz
```

---

### 1️⃣ Human-readable / Binary Extraction

```bash
strings file.bin
strings file.bin | grep "FLAG"
strings file.bin | grep "FLAG" | head -n 1
xxd file.bin | less
xxd -r hexfile.hex > decoded.bin
xxd -p file.bin | tr -d '\n' | xxd -r -p > ascii_output.txt
```

---

### 2️⃣ Base64 Decode

```bash
cat encoded.txt | base64 -d
cat encoded.txt | base64 -d > decoded.txt
strings file.bin | grep -E "^[A-Za-z0-9+/]+={0,2}$" | base64 -d
cat encoded.txt | openssl base64 -d > decoded.txt
```

---

### 3️⃣ ROT13 / Caesar Cipher

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
vim data.txt
# :%!tr 'A-Za-z' 'N-ZA-Mn-za-m'
python3 -c "import codecs; print(codecs.decode(open('data.txt').read(),'rot_13'))"
```

---

### 4️⃣ Hex / Binary Conversion

```bash
xxd file.bin > file.hex
xxd -r file.hex > decoded.bin
xxd -p file.bin | tr -d '\n' | xxd -r -p > ascii_output.txt
```

---

### 5️⃣ URL / Percent Encoding

```bash
python3 -c "import urllib.parse; print(urllib.parse.unquote(open('file.txt').read()))"
python3 -c "import urllib.parse; print(urllib.parse.quote(open('file.txt').read()))"
```

---

### 6️⃣ UUEncode / Decode

```bash
uudecode file.uue
uuencode file.txt file.txt > file.uue
```

---

### 7️⃣ gzip / bzip2 / compress / tar

```bash
# gzip decompress
gzip -d file.txt.gz
gunzip file.txt.gz

# bzip2 decompress
bzip2 -d file.txt.bz2
bunzip2 file.txt.bz2

# tar decompress
tar -xvf archive.tar
tar -xvzf archive.tar.gz
tar -xvjf archive.tar.bz2
```

---

### 8️⃣ Pipe / Kombinasyon Örnekleri

```bash
strings file.bin | grep -E "^[A-Za-z0-9+/]+={0,2}$" | base64 -d
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m' | grep "FLAG"
xxd file.bin | grep "FLAG" | xxd -r > decoded.bin
cat encoded.gz | base64 -d | gunzip
cat encoded.bz2 | bunzip2 | strings | grep "FLAG"
```

---

### 9️⃣ Ekstra / İpuçları

- **file** → dosya türünü öğrenmek için
    
- **mv** → uzantı değiştirmek veya rename
    
- **strings** → binary → ASCII extraction
    
- **grep** → pattern filtreleme
    
- **tr** → ROT13 / karakter dönüşümü
    
- **xxd / hexdump** → hex dump / binary conversion
    
- **base64 / openssl** → Base64 decode
    
- **python / urllib.parse** → URL encode/decode
    
- **uudecode / uuencode** → eski CTF formatları
    
- **gzip / bzip2 / tar** → sıkıştırılmış dosyaları açmak
    

---