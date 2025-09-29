#### **📊 Beef Arayüzüne Erişim**
- Başarılı enjeksiyon sonrası **http://[saldırgan-ip]:3000/ui/panel** adresinden Beef arayüzüne giriş yapılır
- **"Hooked Browsers"** sekmesinde kurbanlar listelenir 🎣
- **"Commands"** sekmesi saldırıların yönetildiği ana bölümdür ⚡

---

### **🚦 Komut Renk Kodlaması**

| Renk | Anlamı | Açıklama |
|------|--------|----------|
| **🟢 Yeşil** | Çalışıyor | Komutun kesin çalışması beklenir |
| **🟡 Turuncu** | Deneysel | Çalışma ihtimali var, test gerekli |
| **🔴 Kırmızı** | Çalışmıyor | Mevcut tarayıcıda çalışması beklenmez |

---

### **🎨 SALDIRI ÖRNEKLERİ**

#### **1. 📸 Ekran Görüntüsü Alma - "Spyder Eye"**
- 🎯 **Amaç:** Kurbanın anlık ekran görüntüsünü alma
- 📁 **Yol:** Commands → "Spyder Eye" modülü
- ⚡ **İşlem:** "Execute" butonuna basıldığında kurbanın ekran görüntüsü alınır
- ✅ **Kullanım:** Hedef izleme, ortam tespiti
#### **2. 🔐 Sosyal Medya Bilgisi Çalma - "Pretty Theft"**

- 🎯 **Amaç:** Sosyal medya hesaplarının kimlik bilgilerini çalma
- 📁 **Yol:** Commands → "Pretty Theft" modülü
- ⚙️ **Ayarlar:**
  - Hangi sosyal medya platformu (Facebook, Twitter, Instagram vb.)
  - Sahte giriş sayfası tasarımı
  - Yönlendirme ayarları
- 🎣 **İşleyiş:** Kurbanın tarayıcısında seçilen platformun sahte giriş sayfası açılır
- 📧 **Sonuç:** Girilen kullanıcı adı/şifre saldırgana iletilir

#### **3. 📥 Zararlı Dosya İndirtme - "Fake Notification Bar"**

- 🎯 **Amaç:** Kullanıcıya backdoor/zararlı yazılım indirtme
- 📁 **Yol:** Commands → "Fake Notification Bar" 
- ⚙️ **Ayarlar:**
  - İndirme mesajı ("Flash Player güncellemesi gerekiyor" vb.)
  - Zararlı dosyanın URL'si
  - Bildirim görünümü
- 🎭 **Psikolojik Taktik:** Kullanıcıyı acil bir güncelleme olduğuna inandırma
- ⚠️ **Risk:** Kullanıcı dosyayı çalıştırırsa **tam sistem erişimi** sağlanır

---

### **🔧 EKLENEBİLECEK DİĞER MODÜLLER**

| Modül | Amaç | Etki |
|-------|------|------|
| **🔑 Keylogger** | Klavye girdilerini kaydetme | Şifreler, mesajlar |
| **🌐 Redirect** | Web sitesi yönlendirme | Phishing sayfalarına |
| **📹 Webcam** | Kamera erişimi | Görüntü alma |
| **📞 Get Internal IP** | Yerel IP öğrenme | Ağ haritalama |

---

### **⚠️ ÖNEMLİ UYARILAR**

1. **🎯 Hedef Seçimi:** Yeşil modüllerle başlayıp, etkiyi test edin
2. **⏰ Zamanlama:** Saldırıları kurbanın aktif olduğu zamanlarda yapın
3. **🔒 Gizlilik:** Fazla saldırı kurbanı şüphelendirebilir
4. **⚖️ Yasal:** Tüm işlemler **sadece test ortamında** yapılmalıdır!

---

### **🚀 İLERİ SEVİYE KULLANIM**

```bash
# Modül Kategorileri:
- Browser Exploits → Tarayıcı zafiyetleri
- Host Exploits → Sistem zafiyetleri  
- Social Engineering → Sosyal mühendislik
- Persistence → Kalıcılık sağlama
```

**✅ Başarılı bir saldırı için:** Doğru modül + Doğru zamanlama + İkna edici sosyal mühendislik 🎭

---