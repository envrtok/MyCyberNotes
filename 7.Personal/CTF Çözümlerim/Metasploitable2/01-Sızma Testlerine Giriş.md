## 🛰️ Nmap ile Cihaz ve Servis Tespiti

- **Nmap**, aynı ağdaki cihazları ve servisleri taramak için kullanılan güçlü bir ağ keşif aracıdır.

- 🚀 Çok sayıda özelliğe sahiptir. Tüm seçenekleri öğrenmek için:
  > 🔎 "nmap cheat sheet" şeklinde arama yaparak kısa yollar ve örnek kullanımlar görüntülenebilir.

---

### 📥 Sonuçları Kayıt Altına Almak

- Tarama sonuçları bir `.txt` dosyasına kaydedilerek verilerin kaybolması önlenebilir.

---

### 🧪 Örnek Tarama (Metasploitable Üzerinden)

- Aşağıdaki komutla detaylı bir tarama yapılabilir:
  ```bash
  nmap -v -sS -A -T4 <hedef ip>
  ```

- Bu komut sayesinde:
  - 🛠️ Açık portlar
  - ⚙️ Servis bilgileri
  - 🖥️ İşletim sistemi tahmini
  - Ve diğer birçok detaylı bilgi elde edilir.

---

📌 **Açıklamalar:**
- `-v` : Ayrıntılı çıktı (verbose)
- `-sS` : Yarı açık (stealth) TCP taraması (SYN scan)
- `-A` : OS tespiti, versiyon bilgisi, script taramaları ve traceroute içerir
- `-T4` : Tarama hızını artırır (daha agresif)

