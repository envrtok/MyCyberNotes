## 1. Web Filtrelerini Atlatma (Bypass Teknikleri)

Hedef sistemdeki web panelleri veya komut satırları belirli kelimeleri (örneğin `cat`) yasaklamış olabilir. Bu durumlarda pes etmek yerine sistemdeki alternatif araçları kullanmak gerekir.

- **Yasaklı Komut:** `cat flag.txt`
    
- **Alternatifler:** - `tac`: Dosyayı sondan başa okur.
    
    - `less` / `more`: Dosya içeriğini sayfa sayfa görüntüler.
        
    - `strings`: Dosya içindeki okunabilir karakterleri ayıklar.
        
    - `grep .`: Dosyanın her satırını eşleştirerek ekrana basar.
        
    - `sort`: Satırları sıralayarak içeriği gösterir.
        

## 2. Arazidekiyle Yaşamak (Living off the Land)

Sisteme dışarıdan araç yüklemek zordur ve iz bırakır. En iyi yöntem, hedef sistemde halihazırda yüklü olan (default) dilleri ve araçları kullanmaktır.

- **Python:** Modern Linux sistemlerinde neredeyse her zaman (`python3`) yüklüdür. Reverse shell için en stabil yoldur.
    
- **Perl / Ruby:** Python'un çalışmadığı veya kısıtlandığı yerlerde (örneğin `pty.spawn` hatası aldığında) alternatif olarak denenmelidir.
    
- **Netcat (nc):** Sisteme yüklü olsa bile güvenlik nedeniyle `-e` (çalıştırma) parametresi silinmiş olabilir. Bu durumda ham TCP bağlantısı kuran diller (Python/Perl) tercih edilmelidir.
    

## 3. Sahte Yemler (Rabbit Holes)

CTF geliştiricileri (ve gerçek saldırganlar) zaman çalmak ve dikkati dağıtmak için bilerek karmaşık ama anlamsız veriler bırakabilir.

- **Örnek:** Kaynak kodunda bulunan ve defalarca decode (Base64 vb.) edilen ama sonunda "Rabbit Hole" çıkan veriler.
    
- **Ders:** Bir ipucu seni çok karmaşık bir yola sokuyor ama yetki vermiyorsa, durup "Bu gerçekten hedefe giden yol mu?" diye sorgula. Büyük resmi kaçırma.
    

## 4. Yetki Yükseltme (Privilege Escalation)

Sisteme giriş yaptıktan sonra (düşük yetkili kullanıcı - örn: `www-data`) ilk kontrol edilmesi gereken yerlerden biri `sudo` yetkileridir.

- **Temel Komut:** `sudo -l`
    
- **Anlamı:** Kullanıcının şifre girmeden (`NOPASSWD`) hangi komutları `root` yetkisiyle çalıştırabileceğini gösterir.
    
- **Zafiyet:** Eğer çıktı `(ALL : ALL) NOPASSWD: ALL` ise, başına `sudo` eklediğin her komut en yüksek yetkiyle çalışır. Bu, sistemin anahtarını teslim almak demektir.