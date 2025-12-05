### **🌐 Dış Ağ (External Network) Nedir?**
Kendi yerel (local) ağımızın dışında kalan, genellikle **İnternet**'in ta kendisi olan, geniş ağdır. 🗺️

---
#### **1. 🔄 Port Forwarding (Port Yönlendirme)**
- **Ne Yapar?:** Yerel ağınızdaki bir cihazın port'u, sizin **public IP** adresinizde belirli bir porta yönlendirilir.
- **Çalışma Mantığı:**
    1.  Kurban, sizin **Public IP**'nize bağlanır.
    2.  Modeminiz/Sisteminiz bu bağlantıyı, iç ağdaki (örneğin backdoor'un çalıştığı) hedef makineye ve porta iletir.
- **⚠️ Risk:** Bu yöntem, saldırganın kendi **Gerçek Public IP**'sini kullanmasını gerektirdiği için **yüksek risklidir** ve kolayca tespit edilebilir. 🔍

#### **2. 🛰️ Tunneling (Tünel Açma) - DAHA GÜVENLİ & GİZLİ**
- **Ne Yapar?:** Ngrok, Cloudflared gibi bir **üçüncü parti tünel servisi** kullanılır.
- **Çalışma Mantığı:**
    1.  Sizin makineniz, tünel servisine sürekli bağlı kalır.
    2.  Tünel servisi size özel, **anonim bir Public URL/IP** verir.
    3.  Kurban bu **anonim URL/IP**'ye bağlandığında, tünel servisi bu bağlantıyı güvenli bir şekilde size yönlendirir.
- **🎭 Avantaj:** Gerçek IP'niz gizli kalır, güvenlik duvarlarını aşmak daha kolay olabilir.

---

### **📊 ÖZET & KARŞILAŞTIRMA**

| Özellik | Port Forwarding 🚪 | Tunneling 🕳️ |
| :--- | :--- | :--- |
| **IP Adresi** | Kendi Public IP'n ❌ | Anonim/Servis IP'si ✅ |
| **Gizlilik** | Düşük 🚨 | Yüksek 🎭 |
| **Kurulum** | Yerel ağda ayar gerekir | Yazılım & Servis tabanlı |
| **Güvenlik** | Riskli ⚠️ | Daha Güvenli 🛡️ |

**Sonuç:** Tunneling, gizlilik ve güvenlik için **kesinlikle daha üstün** bir yöntemdir! 🏆