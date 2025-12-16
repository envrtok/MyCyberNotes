## 📜 Nmap Script Çalıştırmak

- 🔍 Belirli açıklar veya hizmetler hakkında daha detaylı bilgi edinmek için **Nmap scriptleri (NSE - Nmap Scripting Engine)** kullanılabilir.

---

### ⚙️ Kullanım:
```bash
nmap <hedef ip> --script <script_adı> -oN <kayit.txt>
```

- Örneğin:
  ```bash
  nmap 10.0.2.27 --script http-enum.nse
  ```
  - 🔎 Bu komut, **1000 varsayılan portu tarar**, açık portları listeler  
  - Ayrıca HTTP servisi ile ilgili **çok detaylı bilgi** döker.

---

### 📂 Genel Script Çalıştırma
- En çok kullanılan scriptleri çalıştırmak için:
  ```bash
  nmap <hedef ip> -sC
  ```
  - ⚠️ Daha uzun sürer.  
  - Spesifik script kullanımına göre **daha az detaylı bilgi** sağlar.

---

### 🌐 Script Kaynakları
- Tüm NSE scriptlerine ulaşmak için:  
  👉 [https://nmap.org/nsedoc/scripts](https://nmap.org/nsedoc/scripts)

---

📌 **Özet:**  
- `--script` → Belirli bir script çalıştırır (ör. `http-enum.nse`).  
- `-sC` → Varsayılan/popüler scriptleri topluca çalıştırır.  
- `-oN` → Sonuçları `.txt` dosyasına kaydeder.  

---

