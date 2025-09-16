## 🧱 MVC Mimarisi (Model-View-Controller)

**MVC**, yazılım geliştirmede kullanılan bir mimari desendir. Uygulamanın farklı sorumluluklarını birbirinden ayırarak:

- Kodun daha **okunabilir**,
    
- Daha **bakımı kolay**,
    
- Daha **test edilebilir** hale gelmesini sağlar.
    

**MVC bileşenleri:**

1. **Model:**
    
    - Veritabanı işlemleri burada yapılır.
        
    - Veri erişimi, doğrulama ve iş mantığı bu katmanda bulunur.
        
2. **View (Görünüm):**
    
    - Kullanıcıya sunulan arayüzdür.
        
    - Model'den gelen verileri kullanıcıya gösterir.
        
3. **Controller (Denetleyici):**
    
    - Model ve View arasındaki köprüdür.
        
    - Kullanıcının taleplerini işler ve uygun cevabı oluşturur.
        

---

## 🧩 Template Engine (Şablon Motoru)

Template engine’ler, sabit yapılı şablon dosyaları ile dinamik verileri birleştirerek **HTML gibi** çıktılar üretir.

### ✔️ Nasıl çalışır?

**Template Dosyası + Veri (Java Nesnesi vs.) → Template Engine → HTML çıktısı**

### ✔️ Özellikleri:

- İçerisinde sınırlı ölçüde **kod çalıştırma** yeteneği olabilir (örneğin döngüler, değişkenler, koşullar vs.).
    
- Genellikle HTML çıktısı üretmek için kullanılır (örnek: Thymeleaf, Handlebars, EJS, Jinja2).
    

### ⚠️ Güvenlik Zafiyeti: Template Injection

- Eğer kullanıcıdan alınan veri, **doğrudan ve filtresiz şekilde** şablona (template) enjekte edilirse, kötü amaçlı kodlar çalıştırılabilir.
    
- Örn: Kullanıcı girdisi şablon motoruna `"${7*7}"` olarak gönderilirse, bu ifade işlem yapılarak **"49"** dönebilir. Bu, sistemin dışarıdan kod çalıştırabildiğini gösterir.
    

---

## 🧪 Template Engine Test Metodolojisi

Zafiyet taraması ve güvenlik testleri şu adımlarla yapılır:

1. **Tespit:**
    
    - Hedef sistemde bir şablon motoru olup olmadığını belirleme.
        
2. **Tanımlama:**
    
    - Sistemin hangi şablon motorunu kullandığını anlamak için özel girdiler kullanılır.
        
    - Örneğin `${7*7}` yazıldığında "49" dönerse, motor Java tabanlı olabilir. `"{{7*7}}"` gibi farklı sentakslar da test edilir.
        
3. **Sömürme (Exploit):**
    
    - Eğer motor kullanıcı girdisinden kod çalıştırabiliyorsa, sistemde komut çalıştırmak gibi ileri seviye saldırılar yapılabilir.
        
    - Şablon motorunun arkasında çalışan dilin (Java, Python, vb.) özelliklerinden faydalanarak saldırı gerçekleştirilir.
        

---

## 🛡️ Özet & Güvenlik Önlemleri

- Kullanıcıdan gelen veriler **doğrudan şablonlara gönderilmemelidir.**
    
- Şablon motorunun **kod çalıştırma yetenekleri** sınırlanmalı veya devre dışı bırakılmalıdır.
    
- Gerekirse kullanıcı verileri **kaçış karakterleriyle** (escape) güvenli hale getirilmelidir.
    

---

