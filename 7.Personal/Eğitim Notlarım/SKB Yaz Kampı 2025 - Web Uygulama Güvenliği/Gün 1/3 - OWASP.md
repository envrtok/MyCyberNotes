## 📌 **OWASP Nedir?**

**OWASP** (Open Web Application Security Project), web uygulamalarının güvenliği için çalışan, **kar amacı gütmeyen** bir topluluktur. 🌍  
Hedefi:

- Geliştiriciler 👨‍💻
    
- Güvenlik uzmanları 🕵️‍♂️
    
- Sistem yöneticileri 🖥️
    
- Öğrenciler 🎓
    

için **açık ve ücretsiz güvenlik rehberleri** hazırlamak.

🔑 **Ana Kaynakları:**

- 📖 **Cheat Sheet Serisi** → Kısa ve öz uygulama rehberleri
    
- 📊 **OWASP Top 10** → En kritik web güvenlik riskleri listesi
    
- 🛠️ **ZAP** → Ücretsiz web güvenlik testi aracı
    
- 📚 **Proje dokümanları** → Standartlar, metodolojiler, best practice’ler
    

---

## 🏆 **OWASP Top 10 (2021 Versiyonu)**

Bu liste, her siber güvenlik öğrencisinin **ezbere bilmesi gereken** şeylerden biridir.  
İşte güncel liste ve kısa açıklamaları ⬇️

|#|Risk|Açıklama|
|---|---|---|
|🔢 **A01**|**Broken Access Control**|Kullanıcıların yetkisi dışında işlem yapabilmesi 🏴‍☠️|
|🔑 **A02**|**Cryptographic Failures**|Zayıf/yanlış şifreleme kullanımı (örn. şifresiz veri taşıma)|
|🧑‍💻 **A03**|**Injection**|SQL Injection, Command Injection vb.|
|🪪 **A04**|**Insecure Design**|Başından yanlış tasarlanan sistemler|
|📦 **A05**|**Security Misconfiguration**|Yanlış ayarlar, açık debug panelleri, default şifreler|
|🔍 **A06**|**Vulnerable & Outdated Components**|Eski versiyon kütüphaneler, patch uygulanmamış sistemler|
|🔑 **A07**|**Identification & Authentication Failures**|Zayıf oturum yönetimi, tahmin edilebilir şifreler|
|📤 **A08**|**Software & Data Integrity Failures**|Kaynağı doğrulanmamış yazılım güncellemeleri|
|👀 **A09**|**Security Logging & Monitoring Failures**|İzlenmeyen saldırılar, log eksiklikleri|
|🤝 **A10**|**Server-Side Request Forgery (SSRF)**|Sunucunun saldırgana ait kaynağa istek atması|

💡 **Mantık:** Bu liste, uygulamalardaki en yaygın ve en tehlikeli güvenlik açıklarını gösterir. Eğer bu 10 başlığa hakimsen, web güvenliğinde %80 yolu almışsın demektir. 🚀

---

## 🛠️ **OWASP Araçları**

OWASP yalnızca doküman değil, **araçlar** da sunar:

- 🔎 **OWASP ZAP** → Web uygulaması zafiyet tarayıcısı (Burp Suite’e ücretsiz alternatif).
    
- 📚 **Cheat Sheets** → SQL Injection önleme, XSS engelleme, güvenli kimlik doğrulama gibi mini rehberler.
    
- 📖 **ASVS (Application Security Verification Standard)** → Uygulama güvenliği için bir checklist standardı.
    

---

## 🎯 **Ne Bilmeli / Nereden Başlamalı?**

1. **OWASP Top 10’u öğren** (ne olduğunu bil + örnek saldırı senaryosu + nasıl önlenir).
    
2. **ZAP kur ve oyna** (küçük bir test uygulaması üzerinde tarama yap).
    
3. **Cheat Sheet’leri incele** (özellikle giriş seviyesi için XSS, SQLi, Auth).
    
4. **Basit lab’lar çöz** → DVWA, Juice Shop, PortSwigger labs (ücretsiz).
    
5. **Güncel kal** → OWASP her birkaç yılda bir Top 10’u günceller.
    

---

## 🧠 Özet

- **OWASP** = Web güvenliği için **rehber + araç + topluluk**
    
- **OWASP Top 10** = “En yaygın 10 açık” listesi (mülakatlarda klasik soru 🎤)
    
- **İlk Adımın** → Top 10’u ezberle + örnek uygula + ZAP ile pratik yap 🔥
    

---