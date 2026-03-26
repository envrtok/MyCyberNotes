
> **Kategori:** `Access Control` **Zorluk:** `🟢 Apprentice` **Durum:** `✅ Çözüldü` **Tarih:** `2026-02-19` **Lab Linki:** [PortSwigger Academy](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-inconsistent-security-controls)

---

## 📖 Zafiyet Teorisi

### Zafiyet Nedir?

Uygulama, admin paneline erişimi şirket e-posta domainine (`@dontwannacry.com`) göre kısıtlıyor. Ancak kayıt sırasında e-posta doğrulaması yapılırken, sonradan e-posta değiştirme işleminde herhangi bir doğrulama mekanizması bulunmuyor. Bu tutarsızlık, saldırganın e-postasını istediği domaine güncelleyerek admin yetkisi kazanmasına olanak tanıyor.

### Neden Tehlikeli?

Saldırgan gerçek bir `@dontwannacry.com` adresine sahip olmadan admin paneline erişebilir, kullanıcıları silebilir, hassas verilere ulaşabilir ve uygulamanın tüm yönetim fonksiyonlarını ele geçirebilir.

### Hangi Koşullarda Oluşur?

Güvenlik kontrolünün yalnızca belirli bir akışta (kayıt) uygulanıp diğer akışlarda (profil güncelleme) atlanması durumunda oluşur. "Bir yerde kontrol et, her yerde güven" mantığının hatalı uygulanmasıdır.

---

## 🎯 Lab Hedefi

```
Admin paneline erişip carlos kullanıcısını silmek.
```

---

## 🔍 Keşif Aşaması

- Endpoint: `/register` → Kayıt sırasında e-posta doğrulaması var
- Endpoint: `/my-account` → E-posta değiştirme formu mevcut, **doğrulama yok**
- Endpoint: `/admin` → Yalnızca `@dontwannacry.com` domainli kullanıcılara açık
- Gözlem: Kayıt akışı ile profil güncelleme akışı farklı güvenlik kurallarına tabi

---

## 🧩 Exploit Geliştirme

### Adım 1 — Hesap Oluştur

**Payload:**

```
E-posta: herhangi@herhangi.com
```

**Neden?** Uygulamaya erişim sağlamak için gerçek bir hesaba ihtiyaç var. Kayıt sırasında domain kontrolü yok, herhangi bir adres kabul ediliyor.

**Sonuç:** Hesap oluşturuldu, giriş yapıldı.

---

### Adım 2 — E-postayı Şirket Domainine Güncelle

**Payload:**

```
E-posta: mahmut@dontwannacry.com
```

**Neden?** Profil güncelleme endpoint'i e-postayı doğrulamadan kabul ediyor. Gerçek bu adrese sahip olmana gerek yok.

**Sonuç:** E-posta güncellendi, uygulama artık bizi şirket çalışanı olarak görüyor.

---

### Adım 3 — Admin Paneline Eriş ve carlos'u Sil

**Payload:**

```
GET /admin
GET /admin/delete?username=carlos
```

**Neden?** Domain kontrolü geçildiği için `/admin` artık erişilebilir durumda.

**Sonuç:** `carlos` silindi, lab çözüldü. ✅

---

## 🏁 Çözüm

Rastgele bir e-posta ile kayıt olduktan sonra hesap ayarlarından e-postayı `@dontwannacry.com` domainli bir adrese güncelledik. Uygulama bu değişikliği doğrulamadan kabul ettiği için bizi şirket çalışanı olarak tanıdı ve `/admin` paneline erişim sağlandı. Oradan `carlos` kullanıcısı silindi.

---

## ⚙️ Kullanılan Araçlar & Teknikler

|Araç / Teknik|Kullanım Amacı|
|---|---|
|Tarayıcı|Kayıt, profil güncelleme ve admin paneli erişimi|
|Manuel keşif|Akışlar arası tutarsızlığı tespit etmek|

---

## 💡 Kilit Öğrenme Noktaları

1. Güvenlik kontrolleri **tüm akışlarda tutarlı** uygulanmalı; bir yerde kontrol etmek yetmez.
2. E-posta değiştirme gibi kritik işlemler **mutlaka doğrulama gerektirmeli** (eski adrese kod, yeni adrese onay linki).
3. Yetki kontrolü sunucu tarafında **her istek** için ayrı ayrı yapılmalı, kullanıcı verisine körü körüne güvenilmemeli.
4. "Sadece şirket çalışanları erişebilir" gibi kurallar, kullanıcının kendi değiştirebileceği verilere dayandırılmamalı.

---

## ⚠️ Yaygın Hatalar / Dikkat Edilecekler

- E-posta doğrulaması olduğunu varsayıp bu adımı atlamamak — her zaman test et.
- Admin panelinin URL'sini tahmin etmeyi unutmak; `/admin`, `/administrator`, `/panel` gibi yaygın path'leri dene.
- Değişikliğin etkisini görmek için sayfayı yenilemeyi unutmak.

---

## 🔗 Referanslar

- [PortSwigger Academy — Business Logic Vulnerabilities](https://portswigger.net/web-security/logic-flaws)
- [PortSwigger Academy — Access Control](https://portswigger.net/web-security/access-control)
- [HackTricks — Account Takeover](https://book.hacktricks.xyz/pentesting-web/account-takeover)

---

## 🏷️ Etiketler

`#portswigger` `#web-security` `#access-control` `#business-logic` `#apprentice`