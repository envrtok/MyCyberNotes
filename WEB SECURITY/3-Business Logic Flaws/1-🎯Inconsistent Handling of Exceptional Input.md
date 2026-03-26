- 🐛 **Zafiyet Türü:** İş Mantığı Zafiyeti (Business Logic Flaw) & Girdi Kırpma (Input Truncation)
    
- 🔍 **Tespit Etme Yöntemi:** Çok uzun bir e-posta adresi (örn: 255 karakterden fazla) ile kayıt olunduğunda, uygulamanın doğrulama mailini arka planda uzun adrese eksiksiz göndermesine rağmen; "My Account" (Hesabım) sayfasında e-postanın belli bir karakterden sonra (genellikle 255. karakterde) veritabanı tarafından kırpıldığının (truncate edildiğinin) fark edilmesi.
    
- 🛠️ **Sömürü (Exploitation) Adımları:**
    
    1. 📧 Lab sayfasındaki "Email client" üzerinden bize özel tahsis edilen mail sunucu ID'sini (`YOUR-ID.web-security-academy.net`) kopyala.
        
    2. 🧮 Veritabanının e-posta alanını 255 karakterde kırptığını ve hedef sistemde admin yetkisi alabilmek için sonu `@dontwannacry.com` ile biten bir e-postaya sahip olmamız gerektiğini hesapla.
        
    3. ⚙️ `@dontwannacry.com` 17 karakter olduğu için, başına tam 238 adet doldurma karakteri (örn: "a") ekleyip, sonuna da doğrulama mailini alabilmek için kendi sunucu ID'mizi ekleyerek payload'u oluştur: `[238 adet a]@dontwannacry.com.YOUR-ID.web-security-academy.net`
        
    4. 📝 Bu özel hazırlanmış e-posta adresi ve rastgele bir şifre ile sisteme kayıt (Register) ol.
        
    5. ✅ "Email client" sayfasına düşen doğrulama linkine tıklayarak hesabı onayla.
        
    6. 👤 Oluşturulan hesapla giriş yapıp "My Account" sayfasına git ve e-postanın `...aaaaa@dontwannacry.com` olarak başarıyla kırpıldığını teyit et.
        
    7. 👑 Kazanılan şirket içi çalışan yetkisiyle `/admin` paneline erişip `carlos` kullanıcısını sil.
        
- 💡 **Kritik İncelik / Püf Noktası:** Zafiyetin temeli, uygulamanın **e-posta doğrulama servisi** ile **veritabanı kayıt sistemi** arasındaki _kural tutarsızlığıdır_ (Inconsistent handling). Doğrulama sistemi uzunluk limiti olmadan mail atarak onay linkini almamızı sağlarken, veritabanı aynı girdiyi standart 255 karakter limitinde kırparak sistemde `@dontwannacry.com` personeli gibi görünmemizi sağlamıştır. Payload hesabında tam 255. karakterin `.com` ifadesinin `m` harfine denk gelmesini sağlamak (238+17=255) çözümün merkezidir. 🎯