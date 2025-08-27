- 🔑 Bir programı hedef bilgisayar çalıştırdığına, arka planda o programa erişim sağlamamızı **backdoor** kavramı sağlar  
- ✍️ Backdoor baştan **manuel** olarak yazılabileceği gibi, hazır araçlarla da oluşturulabilir  
- 🚀 Bu araçlardan biri **msfvenom**'dur  

---

### 📜 Payload Nedir?
- ⚡ Payload: bir açığı sömürmek için kullanılan **kodlar ve işlemler**dir  
- 🔎 Yapısı:  
```
Platform / Payload Type / Payload Protocol
```
- 🖥️ Örn:  
```
windows/meterpreter/reverse_tcp
```

- Açıklamalar:  
  - 🖼️ **Platform** → hedef makine türü (windows, linux, ios, android, python, java...)  
  - 🔗 **Type** → kurban makine ile saldırgan arasındaki bağlantı şekli (shell, meterpreter ✅ sık tercih edilen, exec, messagebox...)  
  - 📡 **Protocol** → bağlantı yönü (bind ↔️ saldırgan bağlanır / reverse 🔄 kurban bağlanır)  

---

### ⚙️ Msfvenom Kullanımı
- 🔍 Tüm payloadları listelemek için:  
```bash
msfvenom --list payloads
```  

- 📂 Bir payload seçildikten sonra seçenekleri görmek için:  
```bash
msfvenom --payload <secilen_payload> --list options
```  

- ⚙️ Daha sonra gerekli **option konfigürasyonları** (LHOST, LPORT, RHOST vs) ayarlanarak payload hazırlanır  

---

💡 **Özet:**  
Backdoor = hedefe sızmayı kalıcı hale getiren yol  
Payload = açığı sömürmek için kullanılan kod parçası  
Msfvenom = bu payloadları üretmeye yarayan güçlü bir araç 🚀  
