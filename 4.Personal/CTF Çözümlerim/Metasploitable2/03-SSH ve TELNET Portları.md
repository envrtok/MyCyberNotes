## 🔌 SSH ve TELNET

- **SSH (Secure Shell)** ve **TELNET**, bir sunucuya **kullanıcı adı ve parola** ile uzaktan bağlanmayı sağlayan protokollerdir.

---

### 🔐 SSH
- **Tamamen güvenli** bir protokoldür.  
- Veri aktarımı **şifrelenmiş** şekilde yapılır, bu nedenle ağ üzerinde dinleme (sniffing) ile kullanıcı bilgileri ele geçirilemez.

---

### ⚠️ TELNET
- **Güvensiz** bir protokoldür.  
- Veri aktarımı **şifresiz (plain text)** olarak yapılır.
- Eğer ağda **Man in the Middle** saldırısı gerçekleştirilmişse veya **Wireshark** gibi bir paket dinleme aracı kullanılıyorsa, TELNET üzerinden gönderilen kullanıcı adı ve parola **kolayca ele geçirilebilir**.

---

📌 **Özet:**  
- **SSH** → Güvenli ✅  
- **TELNET** → Güvensiz ❌  
