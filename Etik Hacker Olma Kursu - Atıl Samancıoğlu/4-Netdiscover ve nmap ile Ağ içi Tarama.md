- 📡 Ağ içindeki cihazları keşfetmek için **netdiscover** veya **nmap** aracı kullanılır

## 🔍 Netdiscover
- 📌 Kullanım:
  ```bash
  netdiscover -i <interface> -r <ip.ip.ip.0/24> -c <istek sayısı> 
  ```
- 🧪 Örneğin:
  ```bash
  netdiscover -i wlan0 -r 192.168.1.0/24 -c 10
  ```
- ⚙️ **-i** : interface. `ifconfig` ile arayüzü sorgulanabilir.  
- 🌐 **-r** : IP adres aralığı. `ifconfig`'den IP adresi öğrenilip son hanesi `0/24` ile değiştirilir.  
- 🔁 **-c** : istek sayısı. En az 10 istek yapılır, çalışmadığı durumlarda sayı artırılabilir.

---
- 📋 Tarama sonucunda ağdaki IP adresleri ile eşleşen MAC adreslerini listeler.
---

## 🛡️ Nmap
- 📌 Kullanım:
  ```bash
  nmap <ip.ip.ip.10/24> 
  ```
- 📊 Tarama sonucunda IP adreslerini, eşleşen MAC adreslerini, açık portları ve birçok bilgiyi listeler.
- ⚠️ Çok güçlü bir araçtır, bu nedenle **yetkisiz ağlara port taraması yapmak suçtur.**
