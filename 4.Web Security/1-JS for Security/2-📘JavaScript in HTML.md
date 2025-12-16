### 🔹 Running JS

- JS code can be executed directly in the **browser console** (Inspect → Console).
![[Pasted image 20251210214639.png]]
- Page source code can be viewed with **CTRL + U**.

---

### 🔹 Using JS in HTML

- JS is embedded into HTML using the `<script>` tag.
- Two main approaches: **Internal JS** and **External JS**.

---

## 🏠 Internal JS

Code is written directly inside the HTML file:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Internal JS</title>
</head>
<body>
  <h1>Addition of Two Numbers</h1>
  <p id="result"></p>

  <script>
    let x = 5;
    let y = 10;
    let result = x + y;
    document.getElementById("result").innerHTML = "The result is: " + result;
  </script>
</body>
</html>
```

---

## 🌐 External JS

Code is placed in a separate `.js` file and linked via `<script src="...">`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>External JS</title>
</head>
<body>
  <h1>Addition of Two Numbers</h1>
  <p id="result"></p>

  <!-- Link to external JS file -->
  <script src="script.js"></script>
</body>
</html>
```

**script.js**

```javascript
let x = 5;
let y = 10;
let result = x + y;
document.getElementById("result").innerHTML = "The result is: " + result;
```

---

### ✅ Quick Recap

- **Console** → Run JS instantly.
- **Internal JS** → Code inside `<script>` in HTML.
- **External JS** → Code in `.js` file, linked with `<script src="...">`.
- **Source Code** → View with CTRL+U.