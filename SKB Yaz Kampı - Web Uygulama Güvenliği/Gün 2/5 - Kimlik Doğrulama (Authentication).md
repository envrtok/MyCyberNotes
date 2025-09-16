**Kimlik doğrulama**, bir kullanıcının veya uygulamanın gerçekten iddia ettiği kişi/sistem olup olmadığını doğrulama işlemidir.

### Kimler için yapılır?

- **Kullanıcı → Uygulama:** Kullanıcının kendini uygulamaya tanıtması (örn: kullanıcı adı & şifre ile giriş).
    
- **Uygulama → Uygulama:** Bir servisin başka bir servise kimliğini kanıtlaması (örn: API anahtarı ile erişim).
    

---

## 🧾 Basic Authentication

**Basic Authentication**, HTTP istekleri ile birlikte kullanıcı adı ve şifrenin **Base64** formatında gönderildiği en basit kimlik doğrulama yöntemidir.

- Avantaj: Basittir, uygulaması kolaydır.
    
- Dezavantaj: Veriler şifrelenmeden gönderildiğinden **HTTPS kullanılmazsa çok güvensizdir.**
    
- Örnek Header:
    
    ```
    Authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ=
    ```
    

---

## 🔑 Token-Based Authentication

**Token tabanlı kimlik doğrulama**, kullanıcı oturum açtığında bir **token** (jeton) alır. Sonraki isteklerde bu token'ı göndererek kimliğini doğrular.

### Avantajları:

- Sunucu tarafında oturum durumu tutulmaz.
    
- Dağıtık sistemlerde **esneklik** sağlar.
    
- Genellikle **Bearer Token** olarak HTTP header’da gönderilir.
    

### 🚀 JWT (JSON Web Token)

En yaygın token formatlarından biridir. Üç parçadan oluşur:

1. **Header:** Algoritma ve token tipi.
    
2. **Payload:** Kullanıcıya ait bilgiler (id, rol vs.).
    
3. **Signature:** Token'ın bütünlüğünü doğrulayan imza.
    

**Not:** JWT içerisinde hassas veriler _şifrelenmeden_ taşınır, sadece imzalanır. Bu nedenle:

- Kişisel bilgiler, şifreler gibi **gizli veriler JWT içinde taşınmamalıdır.**
    
- Token süresi dolduğunda **geçersiz olur**, ancak kullanıcı kendisi token’ı "yok edemez".
    

---

## 🔐 Multi-Factor Authentication (MFA)

**Çok faktörlü kimlik doğrulama**, oturum açarken birden fazla doğrulama kanıtı isteyen güvenlik yöntemidir.

### Örnek faktörler:

1. **Bildikleriniz:** Şifre
    
2. **Sahip olduklarınız:** SMS doğrulama kodu, e-posta, güvenlik anahtarı
    
3. **Biyometrik:** Parmak izi, yüz tanıma
    

Bu yöntem özellikle **banka sistemleri, kritik altyapılar ve kurumsal uygulamalarda** kullanılır.

---

## 🤖 CAPTCHA (Completely Automated Public Turing test to tell Computers and Humans Apart)

**CAPTCHA**, bir kullanıcının **insan mı yoksa bot mu** olduğunu anlamak için kullanılan güvenlik yöntemidir.

### Amaç:

- Otomatik saldırılara (örneğin form spam, brute force) karşı koruma.
    
- Kullanıcılara görsel, işitsel ya da basit görevler verilir (örnek: “Trafik ışıklarını seç”).
    

---

## 🪓 Brute Force Attack (Kaba Kuvvet Saldırısı)

**Brute Force**, doğru kullanıcı adı ve şifre kombinasyonunu bulmak için **tüm olasılıkları denemeye dayalı** bir saldırı türüdür.

### Özellikleri:

- Otomatik araçlar kullanılarak hızlıca binlerce deneme yapılabilir.
    
- En çok zayıf şifreli sistemlerde etkilidir.
    

### Korunma Yöntemleri:

- CAPTCHA
    
- Hesap kilitleme (belirli denemeden sonra)
    
- Şifre karmaşıklığı zorunluluğu
    
- Rate limiting (belirli aralıklarla deneme izni)
    

---

## 🛡️ Özet

|Yöntem|Açıklama|
|---|---|
|**Basic Auth**|Basit kullanıcı adı/şifre gönderimi|
|**Token Auth (JWT)**|Oturum sırasında alınan token ile kimlik doğrulama|
|**MFA**|Birden fazla doğrulama yöntemiyle güvenliği artırma|
|**CAPTCHA**|Botları engelleme|
|**Brute Force**|Şifre tahmini saldırısı (önlenmeli)|

---
