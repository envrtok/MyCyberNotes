![[Pasted image 20251209171247.png]]

|Component|Segment|Function|
|---|---|---|
|**Scheme**|`http`|Protocol used (e.g., HTTP, HTTPS, FTP)|
|**User Info**|`user:password`|Optional credentials for authentication|
|**Host**|`tryhackme.com`|Domain name or IP address of the server|
|**Port**|`80`|Network port used for the connection|
|**Path**|`/view-room`|Specific resource or endpoint on the server|
|**Query String**|`?id=1`|Key-value pair(s) passed to the server (`id=1`)|
|**Fragment**|`#task3`|Client-side anchor or section reference|

---

## 🔧 Operational Notes

- **Scheme** determines how data is transmitted. `http` is unencrypted; `https` is secure.
- **User Info** is rarely used in modern URLs due to security risks; mostly seen in legacy systems or internal tools.
- **Host** is the server's address. DNS resolves this to an IP. **typosquatting** is called manipulating people with very similar but different host writting. (google.)
- **Port** defaults to `80` for HTTP and `443` for HTTPS unless explicitly specified.
- **Path** maps to a file or route on the server. Often used in RESTful APIs.
- **Query String** is parsed by the server to modify behavior or filter data. Multiple parameters use `&`.
- **Fragment** is never sent to the server. It's used by the browser to scroll or load a specific section.

---
- **typo-squatting** is called manipulating people with very similar but different domain writing. eg:
	- gooogle.com 
	- facebook.corn
	- amazn.com
---

## 🧠 Tactical Reference: URL Parsing in Code

### Python (using `urllib.parse`)

```python
from urllib.parse import urlparse, parse_qs

url = 'http://user:password@tryhackme.com:80/view-room?id=1#task3'
parsed = urlparse(url)

print(parsed.scheme)      # http
print(parsed.username)    # user
print(parsed.password)    # password
print(parsed.hostname)    # tryhackme.com
print(parsed.port)        # 80
print(parsed.path)        # /view-room
print(parse_qs(parsed.query))  # {'id': ['1']}
print(parsed.fragment)    # task3
```