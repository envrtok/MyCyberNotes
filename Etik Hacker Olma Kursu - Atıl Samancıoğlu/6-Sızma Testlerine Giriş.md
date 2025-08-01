- Aynı ağdaki cihazlarda tarama yapmak için kullanılır.
- Çok fazla sayıda özelliği vardır. "nmap cheat sheet" yazılarak ulaşılabilir.
- Tarama sonuçları bir txt'ye kaydedilerek kaybolması önlenir.
- Aşağıdaki taramayı metasploitable üzerinde yaparak inceleyelim.
  ```bash
  nmap -v -sS -A -T4 <hedef ip>
  ```
- Açık portları ve birçok bilgiyi detaylıca getirir.