## 📌 **Burp Suite Nedir?**

Burp Suite, **web uygulamalarını test etmek** için kullanılan bir güvenlik aracıdır.  
🕵️‍♂️ Hacker’ların, pentester’ların, bug bounty avcılarının ve güvenlik araştırmacılarının en çok kullandığı araçlardan biridir.

**Temel İşlevi:**  
📡 Tarayıcı ile internet arasına girer (Proxy 🛰️)  
➡️ Böylece giden ve gelen tüm HTTP/HTTPS trafiğini görebilir, değiştirebilir, yeniden gönderebilirsin.

---

## ⚙️ **Kurulum & İlk Ayarlar**

1. 🔧 **Burp’u indir ve kur** (Community sürümü ücretsizdir).
    
2. 🌐 **Tarayıcı ayarı yap** (proxy olarak `127.0.0.1:8080` ayarla).
    
3. 🔏 **Burp sertifikasını yükle** (HTTPS sitelerde trafiği görebilmek için).
    
4. ✅ Test etmek için bir site aç → Burp’te trafiği görmelisin.
    

---

## 🗂️ **Ana Modüller**

Burp Suite tek bir araç değil, bir **araçlar paketi**dir. İşte en kritik modüller:

### 1️⃣ **Proxy** 🌐

- Tüm HTTP/HTTPS trafiğini yakalar.
    
- İstekleri **durdurabilir (intercept)**, değiştirebilir, göndermeden önce manipüle edebilirsin.
    
- İlk öğrenmen gereken modül bu! 👶
    

### 2️⃣ **Target** 🎯

- Burada hedef siteyi görürsün.
    
- Site haritası (sitemap) çıkarır, hangi endpoint’ler var bakarsın.
    

### 3️⃣ **Repeater** 🔁

- Bir isteği tekrar tekrar göndermeni sağlar.
    
- Manuel testler için çok kullanışlıdır (örneğin SQLi payload’larını denemek).
    

### 4️⃣ **Intruder** 💣 _(Community’de sınırlı)_

- Otomatik saldırılar yapar → Bruteforce, fuzzing vb.
    
- Parametrelerde farklı payload’lar deneyip sonuçları karşılaştırır.
    

### 5️⃣ **Scanner** 🕵️ _(Sadece Pro’da)_

- Otomatik zafiyet taraması yapar.
    

### 6️⃣ **Decoder & Comparer** 🔡

- Veriyi Base64, URL encode/decode yapabilirsin.
    
- İki yanıtı karşılaştırabilirsin.
    

---

## 🧑‍💻 **İlk Pratik – Hello Burp!**

1. Proxy açık → Siteye giriş yap.
    
2. Burp’te **Intercept ON** açık → İlk isteği gör.
    
3. İsteği değiştir:
    

```http
GET / HTTP/1.1
Host: site.com
```

Mesela `User-Agent`’i değiştir → Gönder → Yanıtı incele.  
4. İsteği **Repeater’a yolla** → Oradan tekrar tekrar dene.

💡 **Küçük Örnek:**

- Login formu var → Yanlış şifre gir → İsteği yakala → Parametreyi değiştir → Gönder → Sonucu gör → Bruteforce mantığını öğren.
    

---

## 🎯 **Ne Öğrenmeli?**

1. **Proxy ve Repeater kullanmayı öğren** (manuel test yeteneği kazan).
    
2. **HTTP istek/yanıt yapısını ezberle** (Method, Header, Body).
    
3. **Hedef sitenin endpointlerini keşfet** (Target modülüyle).
    
4. **Intruder mantığını anla** (fuzzing nasıl çalışıyor öğren).
    
5. **Request manipulation pratikleri yap** (XSS, SQLi payload’ları dene).
    

---

## 🏋️‍♂️ **Pratik için Öneriler**

- 🧪 **DVWA** (Damn Vulnerable Web App)
    
- 🍹 **OWASP Juice Shop**
    
- 🎯 **PortSwigger Web Security Academy** (Burp’un geliştiricisi PortSwigger’ın ücretsiz eğitim platformu → Harika interaktif lab’lar var!)
    

---

## 🧠 **Özet**

- Burp Suite = **Tarayıcı ile internet arasındaki adam** 👨‍🚀
    
- En önemli parçalar → **Proxy + Repeater + Intruder**
    
- Önce manuel test, sonra otomasyon → Temeli oturtmadan saldırıya geçme! 🏗️
    
- Bol bol lab çöz → pratik olmadan Burp öğrenilmez! 🏋️‍♂️
    

---