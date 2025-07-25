- WPA ile korunan bir modemin kırılması için ***handshake** sağlanır*, ardından ***wordlist** ile parola kırılmaya çalışılır.

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

