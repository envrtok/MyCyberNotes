## 💉 **Injection (Enjeksiyon)**

**Injection**, kullanıcı girdisi **doğrudan** altyapıya dahil edilirse ortaya çıkar. 🚨  
🔑 Bu durumda saldırgan, sistemin kritik parçalarına müdahale edebilir.

### ⚡ **Neler Yapılabilir?**

- 🗄️ **Veri tabanından veri çalmak**
    
- 🔑 **Yetki yükseltmek / login atlatmak**
    
- 💻 **İşletim sistemi üzerinde komut çalıştırmak**
    
- 🕵️ **Servislerin davranışını değiştirmek**
    

---

## 🖥️ **OS Command Injection**

OS Command Injection = Kullanıcının girdisinin **işletim sistemi komut satırına** enjekte edilmesi.

### 🔗 **Komut Ayırıcılar (Separators)**

Bu karakterler zincirleme komut çalıştırmaya izin verir:

- `&`
    
- `&&`
    
- `|`
    
- `||`
    
- `;`
    

Hem **Windows** hem **Linux**’ta kullanılabilirler. ⚠️

---

### 🧪 **Örnekler**

- 👉 Normal kullanım:
    
    ```
    whoami
    ```
    
    → Kullanıcının kim olduğunu gösterir.
    
- 👉 Enjeksiyonlu kullanım:
    
    ```
    whoami & ping 127.0.0.1
    ```
    
    → Önce kullanıcıyı gösterir, sonra `ping` atar.
    
- 👉 Başka bir örnek:
    
    ```
    ping 127.0.0.1 && whoami
    ```
    
    → `ping`’den sonra **tehlikeli bir komut** çalıştırılabilir.
    

---

## 🚧 **Riskler**

- 📤 Kritik verilerin dışarı sızması
    
- 🔐 Yetki ele geçirilmesi
    
- 🛠️ Sunucuda keyfi komut çalıştırma
    
- 💸 İtibar ve maddi kayıp
    

---

## 🛡️ **Korunma Yöntemleri**

1. 🚫 **Shell çağrılarından kaçın** → Yerine güvenli kütüphane fonksiyonları kullan.
    
2. ✅ **Input validation (Whitelist)** → Sadece beklenen formatı kabul et.
    
3. 📦 **Argümanları ayrı gönder** → Örn: `subprocess.run(["ping", ip])`
    
4. 🔒 **Least privilege** → Uygulama minimum yetkiyle çalışsın.
    
5. 🧩 **Escape/quote** fonksiyonları (zorunlu hallerde).
    
6. 🧱 **Firewall / sandbox** kullan.
    
7. 📜 **Logging & izleme** → Şüpheli girişimleri yakala.
    

---

## 🧠 **Özet**

- **Injection** = Kullanıcı girdisinin kontrolsüzce sisteme dahil edilmesi.
    
- **OS Command Injection** = Shell/komut satırına sızma.
    
- **Sonuç** = Veri kaybı, yetki yükseltme, sistem manipülasyonu.
    
- **Çözüm** = Doğru input validation ✅, shell’den kaçınma 🚫, minimum yetki 🔒.
    

---