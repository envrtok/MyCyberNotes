## 🌐 HTTP ve Durumsuzluk (Statelessness)

### 🔸 HTTP Stateless Nedir?

- HTTP, **stateless (durumsuz)** bir protokoldür.
    
- Her istek, **bağımsızdır**; yani sunucu, önceki isteklerle ilgili herhangi bir **durum bilgisini hatırlamaz**.
    
- Bu yüzden **oturum yönetimi** için çerezler (cookies) ve oturumlar (sessions) gibi mekanizmalara ihtiyaç duyulur.
    

---

## 🍪 Cookie & Session

### Cookie Nedir?

- Tarayıcı (client) tarafından **sunucuya her istekle birlikte gönderilen küçük veri parçalarıdır.**
    
- Genellikle kullanıcıyı tanımlamak için kullanılır (örnek: oturum ID’si taşır).
    

### Session Nedir?

- Sunucu tarafında, **kullanıcıya özel olarak tutulan bilgileri** barındıran objedir.
    
- Cookie, session ID’yi taşır; session’ın kendisi **client tarafında tutulmaz**, sadece sunucudadır.
    
- **Client bu verileri değiştiremez.** (sunucu tarafında yönetildiği için daha güvenlidir)
    

---

## ☠️ CSRF (Cross-Site Request Forgery)

### Tanım:

> **CSRF**, kullanıcının oturumunun açık olduğu bir uygulamada, kötü niyetli bir sitenin onun adına istek göndermesidir.

### 🔍 Senaryo:

1. Kullanıcı **B Bankası**'nda oturum açar.
    
2. Kullanıcı, oturum açıkken **A adlı kötü niyetli siteyi** ziyaret eder.
    
3. A sitesi, kullanıcının tarayıcısında kayıtlı olan oturum bilgilerini (cookie) kullanarak **B Bankası'na istek gönderir** (örneğin para transferi).
    
4. B Bankası, isteğin gerçekten kullanıcıdan geldiğini sanarak işlemi gerçekleştirir.
    

### 🎯 Hedef:

Kullanıcının bilgisi dışında **yetkili işlemler** yaptırmak.

---

### 🛡️ CSRF'ye Karşı Alınabilecek Tedbirler

#### 1. 🚫 GET Metodu ile Durum Değiştirilmemeli

- **GET** istekleri sadece veri almak içindir.
    
- **POST, PUT, DELETE** gibi metotlar kullanılmalı, çünkü **CSRF savunmaları** genelde bu metotlara uygulanır.
    
- Örn:  
    Yanlış → `GET /paraTransfer?miktar=1000`  
    Doğru → `POST /paraTransfer`
    

---

#### 2. 🔐 CSRF Token Kullanımı

- Sunucu, her oturum için **benzersiz bir token** üretir.
    
- Bu token, formun içine gömülür ve istekle birlikte gönderilir.
    
- Sunucu, gelen istekteki token ile oturumdaki token’ı karşılaştırır.
    
- Token eşleşmiyorsa istek reddedilir.
    

### Özellikleri:

- Token, **tahmin edilemez** ve **tek kullanımlıktır**.
    
- Otomatik istekler (örneğin img etiketiyle yapılan istekler) bu token’ı **gönderemez**, bu da saldırıyı önler.
    

---

#### 3. 🍪 SameSite Cookie Ayarları

`SameSite` özelliği, bir çerezin **başka sitelerden gelen isteklere eklenip eklenmeyeceğini** kontrol eder.

|Ayar|Açıklama|
|---|---|
|**Strict**|Çerez sadece aynı site isteklerinde gönderilir. En güvenli seçenektir.|
|**Lax**|Bazı güvenli durumlarda (örn. GET isteği ile geçiş) çerez gönderilebilir. Orta seviye güvenlik.|
|**None**|Çerez her durumda gönderilir. Ancak **HTTPS zorunludur**. En az güvenli olanıdır.|

> 🛑 `SameSite=None` ayarında CSRF riski yüksektir. Güvenlik için `Lax` veya `Strict` tercih edilmelidir.

---

## 📌 Özet

|Konu|Açıklama|
|---|---|
|**HTTP Stateless**|Sunucu istekler arası durum tutmaz|
|**Cookie**|Oturum kimliğini taşır (client tarafında)|
|**Session**|Kimliğe ait verileri sunucu tarafında saklar|
|**CSRF**|Kullanıcının oturumu üzerinden izinsiz işlem yaptırma|
|**Çözümler**|GET yerine POST, CSRF token, SameSite cookie ayarı|

---
