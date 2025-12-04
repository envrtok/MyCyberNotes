### 1. 🏗️ Basic Syntax

```bash
grep [options] "pattern" [file...]
```

- **Pipe Usage:** `cat file.txt | grep "search"`
    

---

### 2. 🧠 Pattern Selection

_Control how `grep` interprets your search query._

|**Option**|**Description**|**Example**|
|---|---|---|
|**`-i`**|**Ignore case** (case-insensitive).|`grep -i "error" log.txt` (Matches "Error", "ERROR")|
|**`-v`**|**Invert match** (select non-matching lines).|`grep -v "success" log.txt` (Show only failures)|
|**`-w`**|Match **whole words** only.|`grep -w "is" file` (Matches "is", ignores "this")|
|**`-x`**|Match **whole lines** only.|`grep -x "Authorized" access.log`|
|**`-E`**|**Extended Regex** (allows `\|`, `+`, `?` without escaping).|`grep -E "warn|
|**`-F`**|**Fixed strings** (literal match, no Regex).|`grep -F ".*" file` (Searches for literal dot-star)|
|**`-P`**|**Perl-Compatible Regex** (PCRE).|`grep -P "\d{3}-\d{4}" phone.txt`|
|**`-f`**|Read patterns from a **file** (one per line).|`grep -f bad_words.txt comments.log`|
|**`-e`**|Specify multiple patterns manually.|`grep -e "warning" -e "error" log.txt`|

---

### 3. 📊 Output Control

_Control what information `grep` prints back to you._

|**Option**|**Description**|**Example**|
|---|---|---|
|**`-c`**|**Count** the number of matching lines.|`grep -c "user" auth.log` (Output: 42)|
|**`-l`**|Print **filenames only** (files with matches).|`grep -l "TODO" *.py`|
|**`-L`**|Print **filenames only** (files **without** matches).|`grep -L "License" src/*`|
|**`-m N`**|Stop reading after **N** matches.|`grep -m 1 "fail" log.txt` (Find first failure)|
|**`-o`**|Show **only matching** part of the line.|`grep -o "http.*" urls.txt` (Extract URLs)|
|**`-q`**|**Quiet** (no output, exit code 0 if found).|`if grep -q "root" users; then echo "Exists"; fi`|
|**`-s`**|**Suppress** error messages (e.g., missing files).|`grep -s "config" /etc/*`|

---

### 4. 🔭 Context Control

_See what happened before or after the match._

|**Option**|**Description**|**Example**|
|---|---|---|
|**`-A N`**|Print **N** lines **After** the match.|`grep -A 3 "Exception" error.log`|
|**`-B N`**|Print **N** lines **Before** the match.|`grep -B 2 "Login failed" auth.log`|
|**`-C N`**|Print **N** lines of **Context** (before & after).|`grep -C 5 "segfault" sys.log`|

---

### 5. 🎨 Formatting & Display

_Add line numbers, colors, and file headers._

|**Option**|**Description**|**Example**|
|---|---|---|
|**`-n`**|Print **line numbers**.|`grep -n "main" script.py` (Output: `10: def main():`)|
|**`--color`**|Highlight matches in color (usually default).|`grep --color=always "mypattern" file`|
|**`-H`**|Print **filename** with each match (Default for multiple files).|`grep -H "var" file.c`|
|**`-h`**|**Suppress filename** prefix.|`grep -h "var" file1.c file2.c`|
|**`-b`**|Print the **byte offset** of the match.|`grep -b "start" data.bin`|

---

### 6. 📂 Directory & File Selection

_How to handle folders, binary files, and exclusions._

|**Option**|**Description**|**Example**|
|---|---|---|
|**`-r`**|**Recursive** (follow directory structure).|`grep -r "function" .`|
|**`-R`**|Recursive (and **follow symlinks**).|`grep -R "config" /etc`|
|**`--include`**|Search only files matching pattern.|`grep -r "import" . --include="*.py"`|
|**`--exclude`**|Skip files matching pattern.|`grep -r "TODO" . --exclude="*.log"`|
|**`--exclude-dir`**|Skip specific **directories**.|`grep -r "key" . --exclude-dir="node_modules"`|
|**`-a`**|Treat **binary files** as text.|`grep -a "string" /bin/ls`|
|**`-I`**|**Ignore binary** files.|`grep -I "text" *`|

---

### 7. 🧩 Basic Regex Quick Reference

_Use these inside your search pattern string._

|**Symbol**|**Description**|**Example**|
|---|---|---|
|**`^`**|Start of line.|`grep "^Root"` (Line starts with Root)|
|**`$`**|End of line.|`grep "false;$"` (Line ends with false;)|
|**`.`**|Any single character.|`grep "b.t"` (Matches bat, bet, bit)|
|**`[]`**|Any character in set.|`grep "[Bb]ob"` (Matches Bob or bob)|
|**`[^]`**|Any character **NOT** in set.|`grep "[^0-9]"` (No numbers)|
|**`*`**|Zero or more of previous char.|`grep "10*"` (Matches 1, 10, 100...)|
|**`\|`**|Or (Requires `-E`).|`grep -E "cat|

---

### 8. 💡 Common Examples

**1. Recursive Search avoiding git and node_modules:**

Bash

```
grep -r "API_KEY" . --exclude-dir={.git,node_modules}
```

**2. Find files containing a string, then delete them (Safe Mode):**

Bash

```
grep -l "deprecated_function" *.js | xargs -p rm
```

**3. Real-time log monitoring (filtering for errors):**

Bash

```
tail -f /var/log/syslog | grep --line-buffered -i "error"
```

**4. Count occurrences of a word:**

Bash

```
grep -o "failure" log.txt | wc -l
```