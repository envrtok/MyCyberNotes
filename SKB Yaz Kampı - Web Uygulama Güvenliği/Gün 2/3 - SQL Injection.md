## 🔹 1. Giriş: SQL Nedir?

- **SQL (Structured Query Language)**, veritabanlarıyla iletişim kurmak için kullanılan bir dildir.
    
- Veritabanında veri **ekleme**, **okuma**, **güncelleme** ve **silme** işlemleri SQL ile yapılır.
    

📌 Örnek SQL sorgusu:

```sql
SELECT * FROM kullanicilar WHERE kullanici_adi = 'ahmet';
```

---

## 🔹 2. Web Formları ve Veritabanı

Birçok web sitesinde kullanıcı adı/şifre giriş formu bulunur.

📌 Örneğin:

```html
<form method="POST" action="giris.php">
  Kullanıcı Adı: <input name="kullanici_adi">
  Şifre: <input type="password" name="sifre">
  <input type="submit" value="Giriş">
</form>
```

Bu form verileri sunucuya gönderir ve sunucu şu şekilde bir SQL sorgusu oluşturabilir:

```sql
SELECT * FROM kullanicilar 
WHERE kullanici_adi = 'kullanici_formdan' AND sifre = 'sifre_formdan';
```

Eğer böyleyse... Tehlike başlıyor!

---

## 🔹 3. SQL Injection Nedir?

Kötü niyetli bir kullanıcı, form alanlarına özel kodlar yazarak SQL sorgusunu manipüle edebilir.

📌 Örnek saldırı:

Kullanıcı Adı kısmına şu yazılır:

```sql
' OR '1'='1
```

Sunucuda oluşan SQL sorgusu şu hale gelir:

```sql
SELECT * FROM kullanicilar 
WHERE kullanici_adi = '' OR '1'='1' AND sifre = '';
```

🧨 Bu sorgu her zaman doğru döner, çünkü `'1'='1'` her zaman doğrudur. Bu da saldırganın **giriş yapmasını sağlar**!

---

## 🔹 4. SQL Injection Örnekleri

### 📌 Örnek 1: Basit Giriş Atlatma

```sql
' OR 1=1 --
```

- `--` işareti, SQL'de yorum satırıdır. Sonraki kısmı yok sayar.
    
- Bu ifade, şifre kontrolünü atlar.
    

---

### 📌 Örnek 2: Veritabanı Bilgilerini Görme

```sql
' UNION SELECT null, version(), null --
```

- Eğer web sayfası kullanıcı bilgilerini ekrana yazıyorsa, bu sorgu veritabanının versiyonunu gösterebilir.
    

---

## 🔹 5. SQL Injection Nasıl Önlenir?

1. ✅ **Hazır sorgular (Prepared Statements)** kullan:
    
    ```php
    $stmt = $db->prepare("SELECT * FROM kullanicilar WHERE kullanici_adi = ? AND sifre = ?");
    $stmt->execute([$kullanici_adi, $sifre]);
    ```
    
2. ✅ **Girişleri doğrula** (örneğin sadece harf/rakam içermeli).
    
3. ✅ **ORM** sistemleri kullan (Laravel, Django gibi).
    
4. ❌ Asla kullanıcı girdisini doğrudan SQL içine yerleştirme!
    

---

## 🔹 6. Pratik Alıştırmalar (Eğitim Amaçlı)

⚠️ Bu alıştırmaları sadece **güvenli, izole edilmiş test ortamlarında** yapın!

- [DVWA - Damn Vulnerable Web Application](https://dvwa.co.uk/)
    
- [bWAPP - Buggy Web Application](http://www.itsecgames.com/)
    
- [HackTheBox](https://www.hackthebox.com/)
    
- [PortSwigger Web Security Academy](https://portswigger.net/web-security/sql-injection)
    

---

## 🔹 7. Gerçek Hayatta Sonuçları

- 🔐 Kişisel verilerin çalınması
    
- 💰 Banka sistemlerinin ele geçirilmesi
    
- 📉 Şirket itibarının zedelenmesi
    
- ⚖️ Yasal sorumluluklar
    

---

## 🎓 Özet

|Konu|Açıklama|
|---|---|
|SQL Nedir?|Veritabanı sorgulama dilidir.|
|SQL Injection Nedir?|Sorguların kötü niyetle değiştirilmesi.|
|Nasıl Çalışır?|Girdi yoluyla sorgulara kod enjekte edilir.|
|Tehlikeleri|Yetkisiz erişim, veri sızıntısı vs.|
|Korunma Yolları|Hazır sorgular, filtreleme, ORM, doğrulama.|
