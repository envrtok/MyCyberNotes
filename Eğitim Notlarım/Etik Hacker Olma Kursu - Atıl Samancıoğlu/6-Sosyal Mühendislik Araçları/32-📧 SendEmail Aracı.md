### **🎯 SendEmail Nedir?**
- **Komut satırından e-posta göndermek** için kullanılan basit ve etkili bir araçtır 💻
- **SSL/TLS desteği** sayesinde güvenli e-posta gönderimi yapabilir 🔒
- Özellikle **sosyal mühendislik** ve **pentest** senaryolarında kullanılır 🎣

---

## **📦 Kurulum & Kontrol**
```bash
# Kali Linux'ta kontrol:
which sendemail

# Kurulum (yoksa):
sudo apt install sendemail -y
```

---

## **⚙️ TEMEL KULLANIM SÖZ DİZİMİ**
```bash
sendemail -f "gonderen@ornek.com" \
    -t "alici@hedef.com" \
    -u "E-posta Konusu" \
    -m "E-posta İçeriği" \
    -s "smtp.sunucu.com:587" \
    -xu "kullanici_adi" \
    -xp "sifre" \
    -o tls=yes
```

---

## **🔧 DETAYLI PARAMETRELER**

### **📋 ZORUNLU ANA PARAMETRELER**
| Parametre | Açıklama | Örnek |
|-----------|----------|--------|
| **-f** | 📨 Gönderen e-posta adresi | `-f "sirket@guvenli.com"` |
| **-t** | 🎯 Alıcı e-posta adresi | `-f "hedef@sirket.com"` |
| **-u** | 📝 E-posta konusu | `-u "ACIL: Şifre Sıfırlama"` |
| **-m** | 📄 E-posta içeriği/metni | `-m "Lütfen şifrenizi sıfırlayın..."` |
| **-s** | 🖥️ SMTP sunucusu ve portu | `-s "smtp.gmail.com:587"` |

### **🔐 KİMLİK DOĞRULAMA PARAMETRELERİ**
| Parametre | Açıklama |
|-----------|----------|
| **-xu** | 🔑 SMTP kullanıcı adı |
| **-xp** | 🔒 SMTP şifresi |
| **-o tls=yes** | 🛡️ TLS şifreleme kullan |

### **📎 DOSYA EKLEME & DİĞER**
| Parametre | Açıklama |
|-----------|----------|
| **-a** | 📎 Dosya eki (attachment) |
| **-cc** | 👥 Bilgi kopyası (CC) |
| **-bcc** | 🕶️ Gizli kopya (BCC) |

---

## **🎭 PRATİK SOSYAL MÜHENDİSLİK SENARYOSU**

### **🛡️ Gmail Örneği:**
```bash
sendemail -f "guvenlik@firma.com" \
    -t "calisan@sirket.com" \
    -u "ACİL: Hesap Doğrulama Gerekiyor" \
    -m "Sayın çalışanımız, hesabınızı doğrulamanız gerekiyor. Linke tıklayın: http://firma-guvenlik.com/dogrulama" \
    -s "smtp.gmail.com:587" \
    -xu "saldirgan@gmail.com" \
    -xp "GMail_Sifresi" \
    -o tls=yes
```

---

## **⚠️ ÖNEMLİ UYARILAR & İPUÇLARI**

### **🔒 GÜVENLİK AYARLARI:**
- **Gmail kullanıyorsanız:** "Daha az güvenli uygulama erişimi" AÇIK olmalı ⚠️
- **2FA etkinse:** Uygulama şifresi kullanmanız gerekir 🔑

### **🎯 SOSYAL MÜHENDİSLİK İPUÇLARI:**
- **Gönderen adı:** Resmi görünen e-posta adresleri kullanın 🏢
- **Konu satırı:** ACİL, ÖNEMLİ, HIZLI gibi kelimeler etkilidir 🚨
- **İçerik:** Resmi dil ve firma logosu ekleyin 📊

### **🐛 SORUN GİDERME:**
```bash
# Debug modu:
-o debug=yes

# SSL sertifikasını doğrulama (test için):
-o tls=no
```

---

## **📊 AVANTAJLAR & DEZAVANTAJLAR**

| ✅ AVANTAJLAR | ❌ DEZAVANTAJLAR |
|--------------|------------------|
| ⚡ Hızlı ve hafif | 📜 Komut satırı - GUI yok |
| 🔧 Scriptlere entegre | 🎨 Formatlama sınırlı |
| 🐧 Linux uyumlu | 📧 Spam filtresine takılabilir |
| 💰 Ücretsiz | 🔐 SMTP ayarları gerekli |

---

**SendEmail, otomasyon ve penetration testing için 🎯 VAZGEÇİLMEZ bir araç!** Doğru kullanıldığında inanılmaz etkili! 😊