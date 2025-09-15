## 🧐 **XSS Nedir?**

**Cross-Site Scripting (XSS)**, bir web uygulamasının kullanıcıdan aldığı veriyi **filtrelemeden/temizlemeden geri döndürmesi** sonucu saldırganın tarayıcıda kendi JavaScript kodunu çalıştırabilmesidir. 🔥

**Sonuç:**

- 🧑‍💻 Kullanıcı verisi çalınabilir (cookies, localStorage).
    
- 🏴‍☠️ Sahte formlar gösterilebilir (phishing).
    
- 🔀 Kullanıcı başka sayfaya yönlendirilebilir.
    
- 💉 Sayfa içeriği manipüle edilebilir.
    

💡 **Kısaca:** XSS = “Kendi kodumu başkasının tarayıcısında çalıştırabiliyorum!” 🕹️

---

## 🔑 **XSS Türleri**

### 1️⃣ Reflected XSS (Yansıyan XSS)

💡 **Mantık:**

- Kullanıcının girdiği veri, **hemen yanıt içinde yansıtılır**.
    
- Kod istek içinde taşınır ve sadece o isteği yapan kişiyi etkiler.
    

🔎 **Örnek:**

```
https://site.com/search?q=<script>alert(1)</script>
```

Eğer site bu inputu filtrelemeden geri döndürürse, tarayıcıda `alert(1)` çalışır.

⚠️ **Kritik:**

- Genellikle linke tıklatma ile sömürülür (phishing).
    
- **Paylaşması kolaydır** çünkü payload URL’de.
    

---

### 2️⃣ Stored XSS (Saklanan XSS)

💡 **Mantık:**

- Saldırgan kodu sunucuya yollar → DB’ye kaydedilir.
    
- Zafiyetli sayfa bu veriyi gösterdiğinde kod **her görene çalışır**.
    

🔎 **Örnek Senaryo:**

- Forum yorumu olarak `<script>alert('XSS')</script>` girersin.
    
- Tüm kullanıcılar sayfayı açtığında script tetiklenir.
    

⚠️ **Kritik:**

- En tehlikeli XSS türüdür çünkü kalıcıdır.
    
- Büyük ölçekli saldırılar (worm’lar) bu yöntemle yayılır.
    

---

### 3️⃣ DOM-based XSS

💡 **Mantık:**

- Sunucu değil, **tarayıcı tarafı (JS kodu)** veriyi yansıtır.
    
- Payload tamamen **DOM manipülasyonundan** tetiklenir.
    

🔎 **Örnek:**

```js
document.write(location.hash);
```

URL’de `#<script>alert(1)</script>` varsa tarayıcıda direkt çalışır.

⚠️ **Kritik:**

- Sunucu log’larında görünmez → Tespiti zor.
    
- SPA (Single Page App) uygulamalarda sık görülür.
    

---

### 4️⃣ Self-XSS

💡 **Mantık:**

- Kullanıcı kendi tarayıcısında kendine payload çalıştırır.
    
- Çoğunlukla sosyal mühendislik ile “Bunu console’a yapıştır, bedava skin kazan!” gibi kandırma senaryolarında kullanılır.
    

⚠️ **Kritik:**

- “Gerçek” bir zafiyet sayılmaz çünkü kurban kendi kendine saldırır.
    

---

## 🔬 **Örnek Payloadlar**

Test için kullanılan basit XSS payload’ları:

```html
<script>alert(1)</script>
<img src=x onerror=alert('XSS')>
<svg/onload=alert(1)>
"><script>alert(1)</script>
```

💡 Bunları **zafiyetli sitelerde** ya da lab ortamında dene (ör. DVWA). **Gerçek sitelerde izinsiz test etme!** ⚠️

---

## 🛡️ **XSS’ten Korunma Yöntemleri**

- 🧼 **Input Validation** → Kullanıcı girdilerini temizle/escape et.
    
- 🔒 **Output Encoding** → HTML, JS, URL context’ine uygun encode et.
    
- 🏷️ **Content Security Policy (CSP)** → Sayfanın hangi script’leri çalıştırabileceğini kısıtla.
    
- 🛠️ **HTTPOnly Cookie** → Cookie’lerin JS ile çalınmasını engelle.
    

---

## 🏋️‍♂️ **Pratik İçin Öneriler**

- 🧪 **DVWA** → XSS seviyelerini dene.
    
- 🍹 **Juice Shop** → XSS görevlerini çöz.
    
- 🎯 **PortSwigger Web Security Academy** → Ücretsiz interaktif XSS lab’ları.
    

---

## 🧠 Özet

- **Reflected XSS** → Anlık yansıma, URL tabanlı.
    
- **Stored XSS** → DB’ye kaydedilir, herkesi etkiler.
    
- **DOM XSS** → JS tarafında tetiklenir.
    
- **Self-XSS** → Sosyal mühendislik, gerçek zaafiyet değil.
    

💡 XSS bilmek, pentest mülakatlarında **olmazsa olmaz**dır. 🎯

---