**Ana Fikir:** Dış ağlarda, sosyal mühendislik ile **BeEF** (Browser Exploitation Framework) kullanılabilir. 🎯

**Yöntem:**
1.  Dış bir sunucuya popüler bir oyun yerleştirilir. 🕹️
2.  Bu oyunun içine **BeEF hook'u** (JavaScript enjeksiyonu) eklenir. ➕

---

### 🗂️ Web Sunucusunu Hazırlama 
```bash
# Mevcut içeriği temizle:
sudo rm -rf /var/www/html/*

# Örnek oyunu (2048) indir:
sudo git clone https://github.com/atilsamancioglu/2048 /var/www/html

# Oyun dosyalarını ana dizine taşı:
sudo mv /var/www/html/2048/* /var/www/html/
```
---

### 🌐 Sistemi Dış Ağa Açma

**1. Basit HTTP Sunucusu Başlatma 🐍**
```bash
# 8000 portunda sunucuyu başlat:
python3 -m http.server 8000
```

**2. Ngrok ile Tünel Açma 🌉**
```bash
# Sunucuyu dış dünyaya aç:
ngrok http 8000
```
-   Ngrok, size özel bir URL verecek (ör: `https://1234-abc.ngrok.io`). ✅
-   Hedef kullanıcılar bu linke tıkladığında, tarayıcıları BeEF kontrolüne girecek. 🎯

---

### ⚠️ Önemli Uyarılar ve Notlar

-   ❗ **Bu yöntem sadece eğitim ve etik hackleme amaçlı kullanılmalıdır.**
-   🔒 **Kendi sisteminizde veya yazılı izniniz olan sistemlerde deneyin.**r.
-   🌐 Ngrok URL'si her başlatmada değişir, statik bir URL için ücretli plan gerekebilir.

---

**Özet:** Bir oyun sitesi kur ➕ Ngrok ile dışarı aç ➕ Hedefi linke çek! 🎣