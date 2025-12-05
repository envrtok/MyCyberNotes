## 🔹 Basic Operations

---

### 📑 Listing & Navigation

- `Get-ChildItem` → for `dir` or `ls`
- `Set-Location` → for `cd`

---

### 📝 Creating & Removing

- `New-Item -Path "<path\new-file>" -ItemType "<file or directory(folder)">` → creates a file or folder
- `New-Item -Path "<path\new-file>"` → removes the given file or folder

---

### 📄 Copying & Reading

- `Copy-Item -Path "<copied-path>" -Destination "<pasted-this-path>"` → copies files or folders
- `Get-Content` → for `type` or `cat`

---

## 🔹 Piping, Filtering, and Sorting Data

---

### 🔗 Piping

- Piping allows output of one command to be input of the next command
    - `command1 | command2`

---

### 📊 Sorting

- `Get-ChildItem | Sort-Object <something>` → sorts by property
    - Properties:
        - Name
        - Length
        - Extension
        - CreationTime
        - Mode
        - FullName
        - LastWriteName
        - LastAccessName
        - ...

---

### 🔍 Filtering

- `Get-ChildItem | Where-Object -Property <PropertyName> -<operator> <Value>`

**Properties:**

- Name
- Length
- Extension
- CreationTime
- ...

**Operators:**

- `EQ` → equals
- `NE` → not equals
- `GT` → greater than
- `GE` → greater or equal
- `LT` → less than
- `LE` → less or equal
- `Like`
- `NotLike`
- ...

**Examples:**

```powershell
Get-ChildItem | Where-Object -Property "Extension" -eq ".txt"
Get-ChildItem | Where-Object -Property "Name" -Like "*ship"
```

---

### 📑 Selecting Properties

- `Get-ChildItem | Select-Object <Properties>` → gives files with given properties

---

### 🔎 Searching Content

- `Select-String -Path "<path>" -Pattern "<pattern>"` → finds files which have given pattern in given path

---