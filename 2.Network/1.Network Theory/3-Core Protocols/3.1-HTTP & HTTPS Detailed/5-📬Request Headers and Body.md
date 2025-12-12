![[Pasted image 20251209180905.png]]
## 🏷️ Request Headers

Request Headers allow extra information to be conveyed to the web server about the request.

### 🔑 Common Request Headers

| 🏷️ Header          | 📌 Example                                                                       | 📖 Description                                                            |
| ------------------- | -------------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| 🌍 **Host**         | `Host: tryhackme.com`                                                            | Specifies the name of the web server the request is for.                  |
| 🖥️ **User-Agent**  | `User-Agent: Mozilla/5.0`                                                        | Shares information about the web browser the request is coming from.      |
| 🔗 **Referer**      | `Referer: https://www.google.com/`                                               | Indicates the URL from which the request originated.                      |
| 🍪 **Cookie**       | `Cookie: user_type=student; room=introtowebapplication; room_status=in_progress` | Stores information the server asked the browser to keep (e.g., sessions). |
| 📄 **Content-Type** | `Content-Type: application/x-www-form-urlencoded`                                | Describes the format/type of data in the request body.                    |

---

## 📦 Request Body

In HTTP requests such as **POST** and **PUT**, data is sent to the server inside the **Request Body**.  
Common formats include **URL Encoded**, **Form Data**, **JSON**, and **XML**.

---

### 🔑 URL Encoded (`application/x-www-form-urlencoded`)

- Data structured as key-value pairs: `key=value`.
- Multiple pairs separated by `&`.
- Special characters are percent-encoded.

**Example:**

```
POST /profile HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0
Content-Type: application/x-www-form-urlencoded
Content-Length: 33

name=Aleksandra&age=27&country=US
```

---

### 📂 Form Data (`multipart/form-data`)

- Allows multiple data blocks separated by a boundary string.
- Supports binary data (e.g., file uploads).

**Example:**

```
POST /upload HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW

----WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="username"

aleksandra
----WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="profile_pic"; filename="aleksandra.jpg"
Content-Type: image/jpeg

[Binary Data Here]
----WebKitFormBoundary7MA4YWxkTrZu0gW--
```

---

### 🧩 JSON (`application/json`)

- Data structured in **name:value** pairs.
- Multiple pairs separated by commas, wrapped in `{ }`.

**Example:**

```
POST /api/user HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0
Content-Type: application/json
Content-Length: 62

{
    "name": "Aleksandra",
    "age": 27,
    "country": "US"
}
```

---

### 🏷️ XML (`application/xml`)

- Data structured inside **tags** with opening and closing markers.
- Tags can be nested.

**Example:**

```
POST /api/user HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0
Content-Type: application/xml
Content-Length: 124

<user>
    <name>Aleksandra</name>
    <age>27</age>
    <country>US</country>
</user>
```