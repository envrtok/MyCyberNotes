- Nmap taramasıyla bulduğumuz her açık **doğrudan exploit edilebilir** anlamına gelmez.  
- Örneğin: **SMTP servisi** üzerinde doğrudan sızma olmayabilir, ancak bilgi toplama yapılabilir.  

---

## 🔍 smtp-user-enum Aracı

- `smtp-user-enum`, SMTP servisinde kullanıcı adlarını tahmin etmeye yarar.  
- Kullanım bilgisi için terminalde yazılır:  

```bash
smtp-user-enum
```

- Örnek kullanım:  

```bash
smtp-user-enum -M VRFY -U <wordlist> -t <hedef ip>
```

- Burada:  
  - `-M VRFY` → VRFY metodunu kullanır.  
  - `-U <wordlist>` → Kullanıcı adlarını içeren wordlist dosyasını belirtir.  
  - `-t <hedef ip>` → Hedef makinenin IP adresi.  

---

## 📂 Wordlist Örneği

- Metasploit’in içinde hazır wordlist bulunur:  

```bash
/usr/share/wordlists/metasploit/namelist.txt
```

---

## 📌 Notlar

- Bu işlem **doğrudan erişim sağlamaz** ❌  
- Ama potansiyel kullanıcı adları tespit edilerek, başka saldırılarda kullanılabilecek değerli bilgiler elde edilir ✅
