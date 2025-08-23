**Nmap**, ağ taraması ve güvenlik testi için kullanılan en popüler araçlardan biridir.  
Aşağıda yaygın kullanılan parametreler ve açıklamaları yer alır.  

---

### 🔹 Temel Kullanım

```bash
nmap <target ip>
```
En önemli **ilk 1000 TCP portu** tarar ve açık olanları listeler.

---

### 🔹 TCP Port Taraması

```bash
nmap <target ip> -sT
```
TCP portlarını tarar (varsayılan tarama türü ile aynı).

---

### 🔹 UDP Port Taraması

```bash
nmap <target ip> -sU
```
UDP portlarını tarar (daha yavaş çalışabilir).

---

### 🔹 Hız Parametreleri

```bash
nmap <target ip> -T0
nmap <target ip> -T5
```
- **T0** → En yavaş, yakalanma riski düşük  
- **T5** → En hızlı, yakalanma riski yüksek  
- Belirtilmezse **T3** varsayılan olarak çalışır.

---

### 🔹 İşletim Sistemi Tespiti

```bash
nmap <target ip> -O
```
Hedefin işletim sistemi bilgilerini tespit etmeye çalışır.

---

### 🔹 Servis / Versiyon Tespiti

```bash
nmap <target ip> -sV
```
Açık portlarda çalışan servislerin versiyon bilgilerini döker.

---

### 🔹 Detay Seviyesi

```bash
nmap <target ip> -v
```
Tarama sırasında yapılan işlemlerin daha detaylı gösterilmesini sağlar.

---

### 🔹 Agresif Tarama

```bash
nmap <target ip> -A
```
İşletim sistemi, versiyon, script taramaları ve traceroute gibi pek çok bilgiyi **tek seferde** toplar.

---

### 🔹 Port Aralığı Belirtme

```bash
nmap <target ip> -p 22-150
```
Belirtilen **22–150** arası portları tarar.

```bash
nmap <target ip> -p-
```
Tüm portları tarar.

---

⚠️ **Not:** Nmap taramaları yalnızca **izinli ağlarda** yapılmalıdır. Aksi takdirde **yasal sorunlara** yol açabilir. 🚫
