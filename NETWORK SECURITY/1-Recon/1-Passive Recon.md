### 1. Passive vs Active Recon

**Passive:** Hedefle doğrudan iletişim kurmadan bilgi toplama. Log bırakmaz, tespit edilmezsin. **Active:** Hedefle doğrudan etkileşim (port scan vb.) — iz bırakır. CTF'te passive önce gelir, hedefe dokunmadan ne kadar bilgi toplayabilirsin?

---

### 2. Whois

Domain/IP hakkında kayıt bilgilerini sorgular.

```bash
whois example.com
```

Verir: Kayıt sahibi, nameserverlar, kayıt/bitiş tarihi, registrar. Bazen e-mail/isim sızıyor.

---

### 3. nslookup & dig

DNS kayıtlarını sorgulamak için.

```bash
nslookup example.com
dig example.com ANY        # tüm kayıtlar
dig example.com MX         # mail sunucuları
dig axfr example.com @ns1  # zone transfer (altın madeni olabilir)
```

A, MX, TXT, CNAME, NS kayıtları — subdomainler ve altyapı hakkında çok şey söyler.
![[Pasted image 20260219162715.png]]

---

### 4. DNSDumpster

Web tabanlı araç → [dnsdumpster.com](https://dnsdumpster.com) Otomatik DNS keşfi + görsel harita çıkarır. Subdomainleri, IP'leri, host ilişkilerini gösterir. CTF'te domain verildiğinde ilk bakılacak yerlerden biri.

---

### 5. Shodan.io

"Cihazların arama motoru." İnternete açık IP/servis/banner bilgilerini indexler.

```
hostname:example.com
port:22 country:TR
```

Açık portlar, servis versiyonları, default credential'lı cihazlar, IoT. CTF'te IP ya da domain verildiğinde Shodan'da aramak çok şey açabilir.

---

**Genel akış:** Whois → dig/nslookup → DNSDumpster → Shodan sırasıyla gidersen hedefe dair kapsamlı bir passive recon yapmış olursun.