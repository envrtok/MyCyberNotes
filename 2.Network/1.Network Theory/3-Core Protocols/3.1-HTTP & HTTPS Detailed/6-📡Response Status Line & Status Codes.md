![[Pasted image 20251209195034.png]]
## 📜 Status Line

The first line in every HTTP response is called the **Status Line**, which contains three parts:

- 📖 **HTTP Version** – The version of HTTP being used.
- 🔢 **Status Code** – A three-digit number showing the outcome of the request.
- 📝 **Reason Phrase** – A short human-readable explanation of the status code.

---

## 🗂️ Status Code Categories

- ℹ️ **Informational (100–199)** – The server has received part of the request and is waiting for the rest.
- ✅ **Successful (200–299)** – The request worked as expected; the server processed and returned data.
- 🔀 **Redirection (300–399)** – The resource has moved; usually provides a new URL.
- ❌ **Client Error (400–499)** – Something is wrong with the request (bad URL, missing authentication, etc.).
- 💥 **Server Error (500–599)** – The server failed while processing the request (server-side issue).

---

## ⭐ Common Status Codes

|🔢 Code|📝 Reason Phrase|📖 Meaning|
|---|---|---|
|100|Continue|The server got the first part of the request and is ready for the rest.|
|200|OK|The request was successful; the server is sending back the resource.|
|301|Moved Permanently|The resource has been permanently moved to a new URL.|
|404|Not Found|The server couldn’t find the resource at the given URL.|
|500|Internal Server Error|Something went wrong on the server’s end; it couldn’t process the request.|
