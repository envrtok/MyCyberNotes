## 1. Shell Türleri: Bind Shell vs. Reverse Shell

Hedef sistemde komut çalıştırma yetkisi (RCE - Remote Code Execution) bulduğumuzda, o sistemle aramızdaki bağlantıyı nasıl kuracağımız hayati önem taşır. Aradaki en büyük fark **"Kim kimi arıyor?"** sorusudur.

- **Bind Shell (Bağlayıcı Kabuk):**
    
    - **Mantık:** Zararlı kod, hedef makinede bir port açar ve _beklemeye başlar_. Biz kendi bilgisayarımızdan o porta gidip bağlanırız. _(Yani arayan biziz)._
        
    - **Neden Genelde Patlar?:** Hedefin önündeki **Güvenlik Duvarı (Firewall)** genellikle dışarıdan içeriye gelen şüpheli bağlantıları (örneğin 4444 portuna yapılan bir isteği) doğrudan engeller.
        
- **Reverse Shell (Ters Kabuk - Altın Standart):**
    
    - **Mantık:** Biz kendi bilgisayarımızda bir port açıp (`nc -lvnp 4444`) _bekleriz_. Hedefteki zararlı kod, içeriden dışarıya çıkarak **bize** bağlantı başlatır. _(Yani arayan hedeftir)._
        
    - **Neden Çok Güçlüdür?:** Güvenlik duvarları dışarıdan gelenlere karşı acımasızken, içeriden dışarıya çıkan trafiğe (egress) genellikle daha güvendiği için (sanki sunucu internette bir yere gidiyormuş gibi), firewall'u atlatmak (bypass) çok daha kolaydır.
        

## 2. Web RCE (Uzaktan Komut Çalıştırma) Hassasiyetleri

Web panellerindeki (örneğin PHP'nin `shell_exec` veya `system` fonksiyonları) zafiyetleri sömürürken, normal bir Linux terminalindeymişiz gibi rahat davranamayız. Web sunucuları anlık işlem yapar ve kapanır, uzun süreli bağlantıları sevmezler.

- **"Self-Contained" (Kendi Kendine Yeten) Payload Zorunluluğu:**
    
    - Web üzerinden gönderilen payload'lar dışarıya (örneğin sistemdeki ortam değişkenlerine) bağımlı olmamalıdır. Bizim IP adresimiz ve Port bilgimiz kodun içine **sert bir şekilde gömülmelidir (hardcoded)**.
        
    - _Hatalı Örnek:_ `export RHOST=10.x.x.x; python3 ... os.getenv("RHOST")` (Web sunucusu değişkeni asıl komuta aktaramadan yolda kaybedebilir ve bağlantı zaman aşımına uğrar).
        
- **Etkileşimli Terminal (TTY) Tuzakları:**
    
    - Reverse shell'i _ilk tetiklediğimiz an_, payload kodunun içine `import pty; pty.spawn("sh")` gibi terminali interaktif hale getiren komutlar koymak genellikle bağlantıyı daha başlamadan koparır. Çünkü web sunucusunun arkasında gerçek bir terminal (TTY) yoktur; kod "terminal bulamadım" diyerek sessizce çöker (Silent Failure).
        
    - **Kural:** İlk bağlantıyı her zaman en çıplak ve temel komutlarla (`subprocess.call(["/bin/sh","-i"])` gibi) kur. TTY yükseltmesini (upgrade işlemi) bağlantı senin Netcat ekranına düştükten _sonra_ yap.
        
