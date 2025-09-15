## 🧐 **Injection Nedir?**

**Injection**, bir uygulamanın kullanıcıdan aldığı veriyi **filtrelemeden / temizlemeden** arka planda bir komut, sorgu veya kod parçasına eklemesi sonucu oluşur.

💡 **Kısaca:**  
Uygulama, saldırganın “veri” olarak verdiği şeyi “komut” gibi algılar → saldırganın kodu çalışır. 🏴‍☠️

---

## 🔑 **Injection Türleri**

### 1️⃣ **SQL Injection (SQLi)** 🗃️

💡 **Mantık:**  
Saldırgan, veritabanına giden SQL sorgusunu manipüle eder.

🔎 **Örnek:**

```sql
SELECT * FROM users WHERE username = '$input'
```

Eğer input = `' OR 1=1 --` olursa:

```sql
SELECT * FROM users WHERE username = '' OR 1=1 --'
```

Bu tüm kullanıcıları döndürür → kimlik doğrulama bypass! 😱

🎯 **Amaç:**

- Kullanıcı bilgilerini çekmek
    
- Şifre hashlerini almak
    
- Yetkileri yükseltmek
    
- Hatta bazı durumlarda **server shell** açmak
    

---

### 2️⃣ **Command Injection** 🖥️

💡 **Mantık:**  
Kullanıcı girdiği veriyi işletim sistemi komutuna enjekte eder.

🔎 **Örnek:**

```php
$ip = $_GET['ip'];
system("ping -c 1 $ip");
```

Input → `8.8.8.8; ls`  
Komut:

```bash
ping -c 1 8.8.8.8; ls
```

Bu hem ping atar hem de sunucudaki dosyaları listeler! 😳

---

### 3️⃣ **LDAP Injection** 📇

💡 **Mantık:**  
LDAP sorgusuna kod eklenir.

🔎 **Örnek:**

```ldap
(&(uid=$input)(userPassword=$pass))
```

Input: `*)(|(uid=*))` → tüm kullanıcılar döner.

---

### 4️⃣ **NoSQL Injection** 📦

💡 **Mantık:**  
MongoDB, CouchDB gibi NoSQL veritabanlarına kötü niyetli JSON enjekte edilir.

🔎 **Örnek:**

```js
db.users.find({ username: input });
```

Input:

```json
{ "$ne": null }
```

Bu tüm kullanıcıları döndürür.

---

### 5️⃣ **Template Injection** 🖋️

💡 **Mantık:**  
Sunucu tarafı template engine (Jinja2, Twig, etc.) içine kod enjekte edilir.

🔎 **Örnek (Python Flask):**

```jinja
Hello {{ name }}
```

Input: `{{7*7}}` → Output: `Hello 49` → Kod çalıştı!

---

### 6️⃣ **Header Injection** 📬

💡 **Mantık:**  
HTTP yanıt header’larını manipüle eder. (ör. CRLF Injection → Response Splitting)

---

## 🧪 **Test İçin Payload Örnekleri**

**SQLi Basit Test:**

```sql
' OR 1=1 --
" OR "1"="1
admin'#
```

**Command Injection Test:**

```bash
; id
&& whoami
| cat /etc/passwd
```

**NoSQL Injection Test:**

```json
{ "$or": [ {}, {"admin": true} ] }
```

---

## 🛡️ **Önleme Yöntemleri**

- ✅ **Prepared Statements (Parametrized Queries)**  
    SQL injection’ın %90’ını öldürür. 🔫
    
- ✅ **Input Validation**  
    Beklenen formatta veri gelmedi mi? → reddet.
    
- ✅ **Least Privilege**  
    DB kullanıcısına minimum yetki ver (sadece SELECT/INSERT gerekiyorsa DELETE/UPDATE yetkisi verme).
    
- ✅ **Escape / Encode**  
    Shell, LDAP, XML, JSON context’lerine uygun kaçış karakterleri uygula.
    

---

## 🏋️‍♂️ **Pratik Öneriler**

- 🧪 **DVWA → SQLi, Command Injection modülleri**
    
- 🏴‍☠️ **bWAPP** → Birçok injection tipi var.
    
- 🎯 **PortSwigger Web Security Academy** → SQLi, NoSQLi interaktif lab’lar.
    
- 🛠️ **sqlmap** → Otomatik SQLi tespiti ve exploitation aracı.
    

---

## 🧠 Özet

- **Injection = Veri → Kod haline geliyor!**
    
- En yaygın tür = **SQL Injection** 🏆
    
- Diğerleri: Command, NoSQL, LDAP, Template…
    
- **En iyi önlem:** Parametrized Query + Input Validation ✅
    

---