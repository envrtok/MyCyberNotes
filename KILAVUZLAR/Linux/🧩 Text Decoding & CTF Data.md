## 1️⃣ Human-readable / Binary Extraction

```bash
# Binary dosyadan ASCII stringleri çıkar
strings file.bin

# Pattern filtrele
strings file.bin | grep "FLAG"

# İlk eşleşmeyi al
strings file.bin | grep "FLAG" | head -n 1

# Hex olarak gör
xxd file.bin | less
xxd -r hexfile.hex > decoded.bin  # Hex'i geri dönüştür
```

---

## 2️⃣ Base64 Decode

```bash
cat encoded.txt | base64 -d
cat encoded.txt | base64 -d > decoded.txt
strings file.bin | grep -E "^[A-Za-z0-9+/]+={0,2}$" | base64 -d
cat encoded.txt | openssl base64 -d > decoded.txt
```

---

## 3️⃣ ROT13 / Caesar Cipher

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
vim data.txt
# :%!tr 'A-Za-z' 'N-ZA-Mn-za-m'
python3 -c "import codecs; print(codecs.decode(open('data.txt').read(),'rot_13'))"
```

---

## 4️⃣ Hex / Binary Conversion

```bash
# Hex encode/decode
xxd file.bin > file.hex
xxd -r file.hex > decoded.bin

# Binary to ASCII
xxd -p file.bin | tr -d '\n' | xxd -r -p > ascii_output.txt
```

---

## 5️⃣ URL / Percent Encoding

```bash
# URL decode (Python)
python3 -c "import urllib.parse; print(urllib.parse.unquote(open('file.txt').read()))"

# URL encode
python3 -c "import urllib.parse; print(urllib.parse.quote(open('file.txt').read()))"
```

---

## 6️⃣ UUEncode / Decode

```bash
# Decode
uudecode file.uue

# Encode
uuencode file.txt file.txt > file.uue
```

---

## 7️⃣ gzip / compress / tar

```bash
# gzip decompress
gzip -d file.txt.gz
gunzip file.txt.gz

# tar decompress
tar -xvf archive.tar
tar -xvzf archive.tar.gz
```

---

## 8️⃣ Pipe / Kombinasyon Örnekleri

```bash
# Binary extraction + Base64 decode
strings file.bin | grep -E "^[A-Za-z0-9+/]+={0,2}$" | base64 -d

# ROT13 decode + grep
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m' | grep "FLAG"

# Hex extraction + decode
xxd file.bin | grep "FLAG" | xxd -r > decoded.bin

# Base64 + gzip
cat encoded.gz | base64 -d | gunzip
```

---

## 9️⃣ Ekstra / İpuçları

- **strings** → binary dosyalardan okunabilir kısmı çıkarır
    
- **grep** → pattern filtrelemede kritik
    
- **tr** → ROT13, karakter dönüşümleri
    
- **xxd / hexdump** → hex dump, binary conversion
    
- **base64 / openssl** → Base64 encode/decode
    
- **python / urllib.parse** → URL encode/decode veya script tabanlı dönüşümler
    
- **uudecode / uuencode** → eski CTF’lerde rastlanır
    
- **gzip / tar / zcat** → sıkıştırılmış dosya içi veriyi çıkarmak
    

---