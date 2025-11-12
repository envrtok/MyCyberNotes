## **🎛️ Controlling the Search Pattern**
*These options change **how** `grep` interprets your search pattern.*

| Option | Description | Example |
| :--- | :--- | :--- |
| **`-i`** | **Ignore case** : Makes the search case-insensitive 🔤 | `grep -i 'error' log.txt` |
| **`-w`** | **Whole word** : Matches only whole words, not partial matches 🎯 | `grep -w 'root' /etc/passwd` |
| **`-v`** | **Invert match** : Shows lines that **do NOT** contain the pattern ❌ | `grep -v 'debug' server.log` |
| **`-E`** | **Extended regex** : Allows powerful patterns with `|` (or), `+`, `?` ⚡ | `grep -E 'warn\|error' messages.log` |

---

## **📊 Controlling the Output**
*These options change **what** `grep` shows when it finds matches.*

| Option | Description | Example |
| :--- | :--- | :--- |
| **`-c`** | **Count** : Shows only the total count of matching lines 🔢 | `grep -c 'failed' auth.log` |
| **`-l`** | **List filenames** : Shows only names of files with the pattern 📄 | `grep -l 'main' *.c` |
| **`-n`** | **Line numbers** : Shows line number before each match #️⃣ | `grep -n 'function' script.js` |
| **`-o`** | **Only matching** : Shows only the exact part that matched ✂️ | `grep -o '[0-9]+' data.txt` |

---

## **📝 Context Control**
*Shows lines **around** your match - super useful for debugging! 🐛*

| Option | Description | Example |
| :--- | :--- | :--- |
| **`-A [num]`** | **After** : Shows match + `[num]` lines **after** it ⬇️ | `grep -A 3 'Exception' app.log` |
| **`-B [num]`** | **Before** : Shows match + `[num]` lines **before** it ⬆️ | `grep -B 2 'denied' security.log` |
| **`-C [num]`** | **Context** : Shows match + `[num]` lines **before & after** it ↔️ | `grep -C 5 'connect' network.log` |

---

## **📂 Directory and File Handling**

| Option | Description | Example |
| :--- | :--- | :--- |
| **`-r`** or **`-R`** | **Recursive** : Searches through all files in directory and subdirectories 🔁 | `grep -r 'API_KEY' /etc/` |

---

### **💡 Pro Tip**
You can combine most options! 🔗
Example: `grep -rin 'database_password' .` 
- **r**ecursively searches 🔁
- **i**gnoring case 🔤  
- shows line **n**umbers #️⃣

This is much more consistent with your previous note-taking style! 🎉