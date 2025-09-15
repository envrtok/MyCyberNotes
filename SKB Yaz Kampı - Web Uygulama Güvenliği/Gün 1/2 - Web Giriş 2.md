## 🏗️ **Document Object Model (DOM)**

DOM, bir web sayfasının **tarayıcı içindeki canlı temsili**dir. 🧠💻

### 🔎 **DOM’un Oluşumu**

1. 📨 **Sunucudan HTML gelir** → HTTP yanıtı içinde.
    
2. 📜 **Tarayıcı HTML’yi parse eder** → Bir ağaç yapısı oluşturur (DOM Tree 🌳).
    
3. 🎨 **CSS yüklenir ve uygulanır** → Sayfa stil kazanır.
    
4. ⚡ **JavaScript çalıştırılır** → DOM manipüle edilebilir hale gelir.
    

### 🛠️ **Görmek için Araçlar**

- 👀 **CTRL + U** → Sunucudan gelen _ham HTML’yi_ görürsün.
    
- 🛠️ **F12 (Developer Tools)** → Tarayıcının oluşturduğu _canlı DOM’u_ görürsün (HTML + JS ile sonradan eklenen öğeler).
    

### ✏️ **DOM ile Etkileşim**

- JavaScript sayesinde sayfanın içeriğini değiştirebilirsin:
    

```js
document.body.style.background = "red"; // Arka planı kırmızı yapar
```

- DOM dinamik olduğundan, JS ile eklediğin veya kaldırdığın her şey **anında** ekranda görünür.
    

---

## 🔒 **Same-Origin Policy (SOP)**

SOP, tarayıcının **güvenlik kuralıdır** ve siteler arası veri sızıntısını engeller. 🛡️

### 🌍 **Origin Nedir?**

Origin = **Protokol + Domain + Port**  
Örnekler:

- `https://example.com:443` ✅
    
- `http://example.com:80` → farklı (protokol farklı!) ❌
    
- `https://api.example.com:443` → farklı (subdomain farklı!) ❌
    

### 🚧 **SOP’un Kuralları**

- 👁️‍🗨️ Bir web sitesi, başka bir sitenin **DOM’una erişemez**.
    
- 📬 Başka origin’den **fetch/XHR isteği** yapabilirsin ama yanıtı okuyamazsın (CORS izni yoksa).
    
- 🏦 Bu kural sayesinde kötü amaçlı bir site, bankanın açık sayfasından verilerini **çalamaz**.
    

### 🎯 **Örnek Senaryo**

- Sen `https://benimsitem.com`’dasın.
    
- JS ile `https://bankam.com`’un DOM’una erişmeye çalıştın.
    
- ❌ Tarayıcı bunu engeller → “Blocked by Same-Origin Policy” hatası alırsın.
    

---

## 🔑 **CORS (Kısaca)**

SOP çok katı bir kuraldır, ama bazen farklı origin’lere erişim gerekir (API çağrıları vb.).  
💡 **CORS (Cross-Origin Resource Sharing)** bu noktada devreye girer:

- Sunucu, yanıt başlığına `Access-Control-Allow-Origin` eklerse, tarayıcı isteğe izin verir.
    
- Böylece SOP kuralı _kontrollü şekilde esnetilir_. 🤝
    

---

## 🧠 **Özet**

- **DOM** = Web sayfasının tarayıcıda yaşayan hali 🧬
    
- **SOP** = Farklı sitelerin birbirine karışmasını engelleyen polis 👮‍♀️
    
- **CORS** = Bu kurala istisna getiren mekanizma 🔑
    

---