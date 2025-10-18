İşte DigitalOcean sunucusuna bağlanma ve oyun kurulum notların düzenlenmiş hali! 🚀

---

### 🔐 Sunucuya Bağlanma 🔗

**SSH Bağlantı Komutu:**
```bash
ssh root@IP_ADRESI
```

**🔍 Bilgiler:**
- **👤 Kullanıcı:** `root`
- **🌐 IP Adresi:** DigitalOcean panelinde görünür
- **🔑 Şifre:** Sunucu oluşturulurken belirlediğin şifre

---

### 🛠️ Apache Kurulumu ve Yapılandırma ⚙️

**1. Apache Kurulumu:**
```bash
# /var klasörüne gitmeye gerek yok, direkt kurabilirsin
sudo apt-get update
sudo apt-get install apache2 -y
```

**2. Web Dizinini Temizleme:**
```bash
cd /var/www/html
sudo rm -f *
```

---

### 🎮 Oyun Kurulumu 🕹️

**1. Oyunu İndir:**
```bash
sudo git clone https://github.com/atilsamancioglu/2048
```

**2. Dosyaları Taşı ve Temizle:**
```bash
# 2048 klasörüne git
cd 2048

# Tüm dosyaları ana dizine taşı
sudo mv * ..

# Ana dizine geri dön
cd ..

# Boş 2048 klasörünü sil
sudo rm -rf 2048
```

---

### ✅ Kurulum Kontrolü ✅

**🌐 Test Et:**
- Tarayıcını aç
- Adres çubuğuna sunucunun **IP adresini** yaz
- 🎉 **2048 oyunu** görünüyorsa başarılı! 🎮

---

### 📝 Komut Özeti 🗒️

```bash
# Sunucuya bağlan
ssh root@IP_ADRESI

# Apache kur
sudo apt-get install apache2 -y

# Web dizinini hazırla
cd /var/www/html
sudo rm -f *

# Oyunu kur
sudo git clone https://github.com/atilsamancioglu/2048
cd 2048
sudo mv * ..
cd ..
sudo rm -rf 2048
```

---

### ⚠️ Önemli Notlar 📌

- ✅ **Apache otomatik başlar** - ekstra ayar gerekmez
- 🌐 **IP adresini** DigitalOcean panelinden bul
- 🔒 **Root erişimi** olduğu için `sudo` kullanımına dikkat
- 🚀 **Kurulum tamamlandığında** oyun herkese açık olur

---

**🎯 Son Durum:** Sunucu hazır! 🎮 Oyun yayında!  
**➡️ Sonraki Adım:** BeEF hook'unu ekle ve oltalamaya başla! 🎣