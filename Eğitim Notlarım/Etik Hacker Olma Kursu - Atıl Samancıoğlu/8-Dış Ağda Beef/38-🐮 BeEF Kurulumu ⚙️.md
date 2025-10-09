**1. Kurulum Konumu 📁**
```bash
# Tercihen /opt klasörüne kurulum önerilir:
sudo git clone https://github.com/beefproject/beef /opt/beef
```

**2. Temel Yapılandırma ⚙️**
```bash
# BeEF klasörüne git:
cd /opt/beef

# Ana config dosyasını düzenle:
sudo nano config.yaml
```

**Yapılacak Değişiklikler:**
- 🔐 **user & passwd:** İstediğiniz kullanıcı adı ve şifreyle değiştir
- 🎯 **metasploit:** `false` → `true` olarak değiştir

**3. Güncellemeleri Çalıştır 🔄**
```bash
# GeoIP veritabanını güncelle:
sudo ./update-geoipdb

# BeEF'i güncelle:
sudo ./update-beef
```

---

### 🔗 Metasploit Entegrasyonu 🎯

**1. Metasploit Config Dosyasına Erişim 📂**
```bash
# Metasploit extension klasörüne git:
cd extensions/metasploit/
sudo nano config.yaml
```

**2. Metasploit Ayarları 🛠️**
```yaml
host: "ngrok_ip_adresi"          # Ngrok'tan alınacak IP
callback_host: "ngrok_ip_adresi" # Ngrok'tan alınacak IP

# Path ayarı (Kali Linux):
path: 
  custom: "/usr/share/metasploit-framework/"
```

---

### 🌐 Ngrok Entegrasyonu 🔄

**Önemli Not:** 
- Ngrok'u `ngrok http 3000` ile başlattıktan sonra
- Forward edilen adresi (örn: `0.tcp.ngrok.io:12345`) al
- Bu adresi yukarıdaki **host** ve **callback_host** alanlarına yaz! ✅

---

### 🎯 Başlatma ve Test 🚀

**BeEF'i Başlat:**
```bash
cd /opt/beef
sudo ./beef
```

**Erişim:**
- 🌐 **BeEF Paneli:** `http://localhost:3000/ui/panel`
- 🔐 Giriş: Config'de ayarladığın kullanıcı adı/şifre

---

### ⚠️ Önemli Hatırlatmalar 📝

- ❗ **Sadece eğitim ve etik hackleme amaçlı kullan!**
- 🔒 **Kendi lab ortamında test et!**
- 📍 Ngrok IP'si her başlatmada değişebilir, config'i güncellemeyi unutma!
- ⚡ Metasploit entegrasyonu daha güçlü exploit imkanı sağlar 💪

---

**Özet:** BeEF kur ➕ Config'leri düzenle ➕ Metasploit'i entegre et ➕ Ngrok'u ayarla ➕ Hedefi beklemeye başla! 🎣