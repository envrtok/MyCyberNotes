### 1. Ping

Hedefin ayakta olup olmadığını kontrol eder. ICMP paketi gönderir.

```bash
ping example.com
ping -c 4 192.168.1.1    # 4 paket gönder
```

TTL değerine bakarak OS tahmini yapılabilir (TTL≈64 → Linux, TTL≈128 → Windows).

---

### 2. Traceroute

Paketi hedefe ulaşana kadar geçtiği tüm hop'ları (router) gösterir.

```bash
traceroute example.com       # Linux
tracert example.com          # Windows
```

Ağ topolojisini anlamak, firewall/IDS nerede devreye giriyor görmek için kullanılır. Bazı hop'lar `* * *` dönebilir (ICMP blokluysa).

---

### 3. Telnet

Bir porta bağlanıp banner grabbing yapmak için klasik yöntem.

```bash
telnet example.com 80
telnet example.com 25
```

Bağlandıktan sonra servis kendini tanıtır (banner) → versiyon, yazılım adı öğrenilir. Artık remote access için kullanılmaz ama port/servis testi için hâlâ işe yarar.

---

### 4. Netcat (nc)

"İsviçre çakısı." Hem banner grabbing hem port scan hem reverse/bind shell için kullanılır.

```bash
nc -nv 192.168.1.1 80       # porta bağlan, banner al
nc -nv -z 192.168.1.1 1-100 # port tarama
nc -lvnp 4444               # listener aç (reverse shell için)
```

CTF'te en sık kullanılan araçlardan biri. Telnet'ten çok daha güçlü.