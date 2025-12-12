## 📦 Variables

- **Definition:** Containers for storing data values.
- **Analogy:** Like labeling a bucket so you can find it later.
- **Declaration Types:**
    - `var` → _function-scoped_
    - `let` → _block-scoped_
    - `const` → _block-scoped, immutable_

---

## 🔤 Data Types

- **Primitive types:**
    - `string` → text
    - `number` → numeric values
    - `boolean` → `true` / `false`
    - `null` → intentional empty value
    - `undefined` → value not assigned
- **Complex type:**
    - `object` → collections (arrays, objects, etc.)

---

## ⚙️ Functions

- **Definition:** A block of code designed to perform a task.
- **Benefit:** Reuse logic without repeating code.
- **Example:**

```javascript
function PrintResult(rollNum) {
    alert("User with roll number " + rollNum + " has passed the exam");
    // additional logic here
}

for (let i = 0; i < 100; i++) {
    PrintResult(rollNumbers[i]);
}
```

---

## 🔁 Loops

- **Purpose:** Repeat a block of code while a condition is true.
- **Types:** `for`, `while`, `do...while`
- **Example:**

```javascript
function PrintResult(rollNum) {
    alert("User with roll number " + rollNum + " has passed the exam");
}

for (let i = 0; i < 100; i++) {
    PrintResult(rollNumbers[i]); // runs 100 times
}
```