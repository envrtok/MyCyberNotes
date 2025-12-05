📦 _Encoding_ → turns readable data ➡️ into coded format  
🔓 _Decoding_ → brings it back ⬅️ to original form

---

### 🔤 **Base64**

**Encode:**

```bash
echo "hello world" | base64
```

➡️ `aGVsbG8gd29ybGQ=`

**Decode:**

```bash
echo "aGVsbG8gd29ybGQ=" | base64 --decode
```

➡️ `hello world`

🧩 _Tip:_ Works great for small text, config, or binary data!

---

### 🧾 **URL Encoding / Decoding**

**Encode:**

```bash
echo "https://example.com?name=John Doe" | jq -sRr @uri
```

➡️ `https%3A%2F%2Fexample.com%3Fname%3DJohn%20Doe`

**Decode:**

```bash
echo "https%3A%2F%2Fexample.com%3Fname%3DJohn%20Doe" | jq -sRr @urldecode
```

➡️ `https://example.com?name=John Doe`

🌐 _Handy for APIs & web scripts!_

---

### 🧮 **Hex Encoding**

**Encode:**

```bash
echo -n "Hi" | xxd -p
```

➡️ `4869`

**Decode:**

```bash
echo -n "4869" | xxd -p -r
```

➡️ `Hi`

💡 _Used often in low-level tools or binary analysis._

---

### 🔢 **Binary Encoding**

**To binary:**

```bash
echo -n "A" | od -An -t u1 | awk '{for(i=1;i<=NF;i++)printf("%08d\n", strtonum("0b" sprintf("%08d", $i)))}'
```

(🧠 Ok that’s overkill, but you can use `xxd` or `hexdump` instead 😅)

---

### 🗃️ **File Encoding Check**

```bash
file -i filename.txt
```

➡️ `text/plain; charset=utf-8`

**Convert encoding (UTF-8 → ISO-8859-1):**

```bash
iconv -f UTF-8 -t ISO-8859-1 input.txt -o output.txt
```

🌈 _iconv = your best friend for encoding conversions!_

---

### 🧰 **Quick Summary**

|🔧 Tool|💬 Use|
|---|---|
|`base64`|Text ↔ Base64|
|`xxd` / `hexdump`|Text ↔ Hex|
|`jq`|URL encode/decode|
|`iconv`|Charset conversion|
|`file`|Detect encoding|
