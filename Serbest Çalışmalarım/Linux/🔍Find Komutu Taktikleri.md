## 📂 1. Dosya Türü

```bash
find . -type f        # Normal dosyalar
find . -type d        # Dizinler
find . -type l        # Sembolik linkler
find . -type b        # Block device
find . -type c        # Character device
find . -empty         # Boş dosya/klasörler
```

---

## 📝 2. İsim & Desen

```bash
find . -name "*.txt"          # Belirli uzantı
find . -iname "*.jpg"         # Büyük/küçük harf duyarsız
find . ! -name "*.bak"        # Hariç tut
find . -regex ".*\.sh"        # Regex ile eşleşen
find . -iregex ".*\.(jpg|png)"# Regex + case-insensitive
```

---

## 📏 3. Boyut

```bash
find . -size +100M       # 100MB'dan büyük
find . -size -10k        # 10KB'dan küçük
find . -size 1G          # Tam 1GB
find . -size 1033c       # Tam 1033 byte 
```

---

## ⏰ 4. Zaman

```bash
find . -mtime -7        # Son 7 günde değişmiş
find . -mtime +30       # 30 günden eski
find . -mmin -10        # Son 10 dakikada değişmiş
find . -ctime -2        # Son 2 günde izin/sahiplik değişmiş
find . -atime -1        # Son 24 saatte erişilmiş
find . -newer file.txt  # Belirli dosyadan yeni olanlar
```

---

## 🔑 5. İzinler & Erişim

```bash
find . -perm 644        # Tam 644 izinli
find . -perm -o=w       # Herkese yazılabilir
find . -executable      # Çalıştırılabilir dosyalar
find . ! -executable     # Çalıştırılamayan dosyalar 
find . -readable        # Okunabilir dosyalar
find . -writable        # Yazılabilir dosyalar
```

---

## 👤 6. Kullanıcı & Grup

```bash
find . -user enver       # Belirli kullanıcıya ait
find . -group www-data   # Belirli gruba ait
find . -nouser           # Kullanıcısı olmayan
find . -nogroup          # Grubu olmayan
```

---

## 🔢 7. İleri Seviye & CTF İçin Özel

```bash
find . -links +1           # Birden fazla hardlink
find . -inum 12345         # Belirli inode
find . -samefile a.txt     # Aynı inode’daki dosyalar
find . -fstype ext4        # Belirli FS türünde ara
find . -prune              # Belirli dizinleri hariç tut
find . -maxdepth 2         # 2 seviye derine kadar
find . -mindepth 3         # 3. seviyeden sonrası
find / -mount              # Sadece aynı dosya sisteminde
find . -quit               # İlk bulduktan sonra çık
```

---

## ⚡ 8. İşlem (Action)

```bash
find . -print                   # Varsayılan: yazdır
find . -ls                      # ls -dils formatında göster
find . -printf "%p %s bytes\n"  # Özel çıktı formatı 
find . -exec ls -lh {} \;       # Human-readable boyut ile listele
find . -exec rm {} \;           # Bulunanları sil
find . -exec mv {} /tmp/ \;     # Taşı
find . -exec chmod 644 {} \;    # İzin değiştir
find . -ok rm {} \;             # Silmeden önce sor
find . -delete                  # Direkt sil
find . -print0 | xargs -0 cmd   # Xargs ile hızlı işlem
```

---

## 🎯 9. CTF ve Güvenlik Senaryoları

```bash
find / -perm -4000 2>/dev/null          # SUID bitli dosyalar
find / -perm -2000 2>/dev/null          # SGID bitli dosyalar
find / -type f -perm -o+w 2>/dev/null   # World-writable dosyalar
find / -type f -user root -perm -o+w 2>/dev/null # Root’a ait world-writable
find / -type f -name "*.sh" 2>/dev/null # Shell scriptleri
find / -type f -name "id_rsa*" 2>/dev/null # SSH anahtarları
find / -type f -name "*.conf" 2>/dev/null   # Config dosyaları
find / -type f -exec grep -li "password" {} \; 2>/dev/null # Şifre içeren dosyalar
find . -size 1033c -exec ls -lh {} \;      # 1033 byte, human-readable, CTF
find . ! -executable -size 1033c -exec ls -lh {} \;  # Not executable, 1033 bytes
```

---