![[Pasted image 20251209180905.png]]

- HTTP Requests have 3 main components: **Request Line**, **Headers**, and **Body**.

## 1️⃣ Request Line

- 📡 Tells the server what kind of request is sent.
- Contains: **HTTP method**, **URL path**, and **HTTP version**.
- Structure: `Method / Path / Version`
    - 🔨 **Method** – Action the client wants.
    - 📍 **Path** – Location of the resource.
    - 📖 **Version** – HTTP version used.

---

### ⚡ HTTP Methods

- 🔎 **GET** – Retrieve data from the server.
- 🧾 **HEAD** – Same as GET but only headers.
- 📤 **POST** – Send data to create/update resources.
- ✍️ **PUT** – Replace a resource entirely.
- 🩹 **PATCH** – Apply partial changes.
- 🗑️ **DELETE** – Remove a resource.
- ❓ **OPTIONS** – Ask which methods are supported.
- 🔗 **CONNECT** – Create a tunnel (e.g., HTTPS).
- 🪞 **TRACE** – Echo request for debugging.

---

### 📚 HTTP Versions

- 🍼 **HTTP/0.9** – Very basic, only GET supported.
- 📜 **HTTP/1.0** – Added headers & status codes, but no persistent connections.
- 🔄 **HTTP/1.1** – Persistent connections, chunked transfers, caching.
- 🚄 **HTTP/2** – Multiplexing, faster & more efficient.
- 🌐 **HTTP/3** – Uses QUIC, lower latency & better reliability.