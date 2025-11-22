### 🔍 Basic Usage

- `grep PATTERN file` → Search for text in a file

---

### 🎯 Matching Options

- 🆎 `-i` → Ignore case (match `Hello`, `HELLO`, `hello`)
- 🎯 `-w` → Match whole words only (no partial matches)
- 📏 `-x` → Match entire line exactly

---

### 📂 File Control

- 📑 `-r` or `-R` → Recursive search in directories
- 🗂️ `-l` → Show only filenames with matches
- 🗂️❌ `-L` → Show only filenames _without_ matches

---

### 📊 Output Control

- 🔢 `-n` → Show line numbers with matches
- ➕ `-c` → Count number of matching lines
- 📜 `-o` → Show only the matching part of the line
- 🖼️ `--color=auto` → Highlight matches in color

---

### 📍 Context Control

- 👀 `-A NUM` → Show NUM lines _after_ match
- 👀 `-B NUM` → Show NUM lines _before_ match
- 👀 `-C NUM` → Show NUM lines _around_ match

---

### ⚡ Performance / Special

- 🚀 `-q` → Quiet mode (no output, just exit status)
- 🧩 `-e PATTERN` → Specify multiple patterns
- 🧮 `-E` → Use extended regex (like `egrep`)
- 🧮 `-P` → Use Perl regex (powerful, but not always available)

---

### 🧪 Examples

```bash
grep -i "error" logfile.txt     # 🔍 Case-insensitive search
grep -n "main()" *.c            # 📑 Show line numbers in C files
grep -r "TODO" src/             # 📂 Search recursively in src/
grep -A2 "failed" system.log    # 👀 Show 2 lines after "failed"
grep -c "hello" notes.txt       # ➕ Count matches
```

---

⚡ **Pro tip:** Combine options! Example:  
`grep -rin --color=auto "bug" ./src` → Recursive, case-insensitive, show line numbers, highlight matches 🎨.