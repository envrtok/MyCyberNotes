### **🤔 Nedir Bu Tünel Servisleri?**
- **Yerel bilgisayarınızda** çalıştırdığınız özel servislerdir. 💻
- Yerel ağınızdaki **sunucuları tüm İnternet'e açar** - güvenlik duvarı sorununu çözer! 🌐
- Dış dünyadan gelen bağlantıları **yakalar** ve sizin dinlediğiniz porta **yönlendirir**. 🔄

---

## **📥 Ngrok Kurulum Adımları**

1.  **🌐 Kayıt & Giriş**
    - `ngrok.com`'a gir → Hesap oluştur → Giriş yap ✅

2.  **⬇️ Programı İndir**
    - Dashboard'dan ngrok'u indir → ZIP'ten çıkar 📂

3.  **🔑 Token Ayarları**
    - Arayüzdeki **authtoken**'ı kopyala
    - Terminal'de şu komutu çalıştır:
    ```bash
    ./ngrok config add-authtoken [TOKEN_BURAYA]
    ```
    - **✅ Kurulum tamam!**

---

## **🎮 Ngrok Kullanımı**

### **🆘 Yardım Almak**
```bash
./ngrok help
```
Tüm komutları ve kullanım detaylarını gösterir. ❓

### **🚀 TCP Port Açmak**
```bash
./ngrok tcp 4242
```
**Ne Yapar?** 🔍
- Ngrok sunucusunda **sanal bir port** açar
- Dışarıdan gelen tüm bağlantılar, sizin **yerel 4242 portunuza** yönlendirilir
- **Arayüzde görünen adres** → Sizin gerçek portunuza tünel! 🎯

---

### **💡 Önemli Hatırlatma**
Ngrok sayesinde **Public IP paylaşmadan**, güvenli bir şekilde dış bağlantı alabilirsiniz! 🛡️ Süper praktik! 😊