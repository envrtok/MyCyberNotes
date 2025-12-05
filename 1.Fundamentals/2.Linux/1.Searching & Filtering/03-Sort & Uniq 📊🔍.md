# 🔢 `sort` 

`sort` arranges lines of text files. By default, it sorts alphabetically (ASCII order).

### 1. 🏗️ Basic Syntax

```bash
sort [options] [file]
```

### 2. 🔀 Ordering Options

_Control the direction and logic of the sort._

|**Option**|**Description**|**Example**|
|---|---|---|
|**`-r`**|**Reverse** order (descending).|`sort -r names.txt` (Z to A)|
|**`-R`**|**Random** sort (shuffle).|`sort -R playlist.txt`|
|**`-f`**|**Ignore case** (fold case).|`sort -f list.txt` (Apple == apple)|
|**`-V`**|**Version** sort (natural numbers).|`sort -V versions.txt` (v2 comes before v10)|
|**`-u`**|**Unique** (remove duplicates).|`sort -u ids.txt` (Sorts AND removes dupes)|

### 3. 🔢 Numeric Sorting

_Crucial because standard sort treats "10" as coming before "2"._

|**Option**|**Description**|**Example**|
|---|---|---|
|**`-n`**|**Numeric** sort (string numerical value).|`sort -n numbers.txt` (1, 2, 10)|
|**`-h`**|**Human-readable** numbers (K, M, G).|`sort -h sizes.txt` (2K, 1M, 3G)|
|**`-g`**|**General numeric** (supports scientific e.g., 1e10).|`sort -g scientific.dat`|

### 4. 🎯 Columns & Fields (`-k` and `-t`)

_Sort by specific columns instead of the whole line._

|**Option**|**Description**|**Example**|
|---|---|---|
|**`-t 'sep'`**|Define **separator** (default is whitespace).|`sort -t ',' data.csv` (Use comma for CSV)|
|**`-k N`**|Sort starting at field **N**.|`sort -k 2 data.txt` (Sort by 2nd column)|
|**`-k N,M`**|Sort by key start **N** to end **M**.|`sort -k 2,2 data.txt` (Sort ONLY by 2nd col)|
|**`-k Nnr`**|Add flags to specific keys (numeric, reverse).|`sort -k 2nr scores.txt` (2nd col, numeric reverse)|

### 5. ⚙️ Operational Options

|**Option**|**Description**|**Example**|
|---|---|---|
|**`-o [file]`**|**Output** to file (safe in-place edit).|`sort file.txt -o file.txt`|
|**`-c`**|**Check** if file is already sorted.|`sort -c file.txt` (No output if sorted)|
|**`-m`**|**Merge** already sorted files (faster).|`sort -m sorted1.txt sorted2.txt`|
|**`-b`**|**Ignore leading blanks** (spaces).|`sort -b indented.txt`|

---

# 🦄 `uniq` 

uniq filters or reports repeated lines.

⚠️ Important: uniq only detects adjacent duplicate lines. You must run sort before uniq.

### 1. 🏗️ Basic Syntax

``` bash
uniq [options] [input_file] [output_file]
```

### 2. 🕵️‍♂️ Filtering Logic

_Decide which lines to keep or hide._

|**Option**|**Description**|**Example**|
|---|---|---|
|**(None)**|Removes adjacent duplicates.|`uniq names.txt`|
|**`-d`**|Show **duplicates only** (one per group).|`uniq -d names.txt` (Show names appearing > once)|
|**`-D`**|Show **all duplicate** lines.|`uniq -D names.txt` (Prints every repeated line)|
|**`-u`**|Show **unique only** (lines that appear exactly once).|`uniq -u names.txt` (Hides anything repeated)|
|**`-i`**|**Ignore case** when comparing.|`uniq -i list.txt` ("ABC" matches "abc")|

### 3. 📊 Counting & Formatting

_Analyze the frequency of lines._

|**Option**|**Description**|**Example**|
|---|---|---|
|**`-c`**|**Count** occurrences (prefix with number).|`uniq -c ips.txt` (Output: `5 192.168.1.1`)|
|**`-z`**|Null-terminated output (for `xargs -0`).|`uniq -z filenames.txt`|

### 4. 🙈 Ignoring Data

_Skip parts of the line when comparing._

|**Option**|**Description**|**Example**|
|---|---|---|
|**`-f N`**|Skip the first **N fields** (columns).|`uniq -f 1 log.txt` (Ignore timestamp in col 1)|
|**`-s N`**|Skip the first **N characters**.|`uniq -s 4 data.txt` (Skip "ID: " prefix)|
|**`-w N`**|Compare **only** the first **N characters**.|`uniq -w 10 longlines.txt`|

---

### 🤝 The "Power Combo" Examples

_Since `uniq` needs sorted input, these two are usually piped together._
#### 1. The "Frequency Count" (Most common command):
- Find top 5 output items.

``` bash
sort access.log | uniq -c | sort -nr | head -5
```
1. `sort`: Groups duplicates.
	
2. `uniq -c`: Counts them.
	
3. `sort -nr`: Sorts by count (Numeric, Reverse).
	
4. `head -5`: Shows top 5.
	    
#### 2.CSV Sorting:
Sort a CSV file by the 3rd column (Price), numerically.

```
sort -t ',' -k 3n products.csv
```

#### 3.Extract Duplicate IP addresses:

Find IPs hitting your server more than once.

```bash
sort server.log | uniq -d
```
