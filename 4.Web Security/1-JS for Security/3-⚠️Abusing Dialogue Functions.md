### 🎯 Purpose

- JS provides **dialogue boxes** (`alert`, `prompt`, `confirm`) for user interaction and dynamic content updates.
- If misused, these can be exploited (e.g., **XSS attacks**) to disrupt or compromise user experience.

---

## 🔹 Alert

- Displays a message with an **OK** button.
- Used for **information** or **warnings**.

```javascript
alert("Hello THM");
```

👉 Try in Chrome Console → `alert("Hello THM")` → dialogue box appears.
![[Pasted image 20251210215256.png]]

---

## 🔹 Prompt

- Displays a box asking for **user input**.
- Returns the entered value or `null` if **Cancel** is clicked.

```javascript
name = prompt("What is your name?");
alert("Hello " + name);
```

👉 Run in Console → input box appears → greets user with entered name.
![[Pasted image 20251210215304.png]]

---

## 🔹 Confirm

- Displays a box with **OK** and **Cancel**.
- Returns `true` if **OK**, `false` if **Cancel**.

```javascript
confirm("Do you want to proceed?");
```

👉 Run in Console → returns `true` or `false` depending on choice.
![[Pasted image 20251210215312.png]]

---

## 🚨 Exploitation Example

Attackers can abuse these functions to **annoy or trap users**:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Hacked</title>
</head>
<body>
  <script>
    for (let i = 0; i < 3; i++) {
      alert("Hacked");
    }
  </script>
</body>
</html>
```

- Opening this file (`invoice.html`) → shows **3 alert boxes**.
- If loop count = `500` → user is forced to close hundreds of alerts.

---

## ✅ Key Takeaways

- Dialogue functions are **simple but powerful**.
- **Malicious use** can cause inconvenience or worse.
- Always run JS from **trusted sources only**.

---

📊 **Quick Comparison Table**

|Function|Purpose|Return Value|Example Code|
|---|---|---|---|
|`alert`|Show info/warning|None|`alert("Hello THM");`|
|`prompt`|Ask for input|User input / `null`|`prompt("What is your name?");`|
|`confirm`|Ask for confirmation|`true` / `false`|`confirm("Do you want to proceed?");`|
