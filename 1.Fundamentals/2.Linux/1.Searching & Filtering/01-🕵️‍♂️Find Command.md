### 1. 🏗️ Basic Syntax

The structure is strict: **Options** first, then **Path**, then the **Expression** (Tests & Actions).

``` bash
find [options] [path] [expression]
```

---

### 2. ⚙️ Global Options

_These appear **before** the path and control how `find` handles links and optimization._

|**Option**|**Description**|**Example**|
|---|---|---|
|**`-P`**|**Default.** Check the symlink itself, not the target.|`find -P . -name "mylink"`|
|**`-L`**|Follow symbolic links to their targets.|`find -L /var/www -name "index.html"`|
|**`-H`**|Follow symlinks **only** if they are command line arguments.|`find -H symlink_to_docs -name "*.pdf"`|
|**`-D [type]`**|Print debug info (`tree`, `stat`, `opt`, `rates`).|`find -D tree . -name "test"`|
|**`-O[0-3]`**|Optimization level (3 is highest).|`find -O3 / -name "lostfile"`|

---

### 3. 🚧 Positional Options (Boundaries)

_These limit **where** `find` looks._

|**Parameter**|**Description**|**Example**|
|---|---|---|
|**`-maxdepth N`**|Descend at most _N_ levels.|`find . -maxdepth 1 -name "*.txt"` (Current dir only)|
|**`-mindepth N`**|Start looking only at level _N_.|`find . -mindepth 2 -name "*.conf"` (Skip current dir)|
|**`-mount`** / **`-xdev`**|Don't go to other filesystems (e.g., skip USBs).|`find / -xdev -name "*.log"` (Stays on root drive)|
|**`-ignore_readdir_race`**|No error if a file is deleted during search.|`find /tmp -ignore_readdir_race -name "cache*"`|

---

### 4. 🔍 Tests (The Filters)

#### A. 🏷️ By Name & Regex

|**Parameter**|**Description**|**Example**|
|---|---|---|
|**`-name`**|Case-sensitive filename match.|`find . -name "Image.png"`|
|**`-iname`**|Case-insensitive filename match.|`find . -iname "image.png"` (Matches Image.PNG)|
|**`-path`**|Matches the full path string.|`find . -path "./src/test/*.js"`|
|**`-ipath`**|Case-insensitive path match.|`find . -ipath "./SRC/TEST/*.js"`|
|**`-regex`**|Match whole path with Regex.|`find . -regex ".*-[0-9]+\.jpg"`|
|**`-iregex`**|Case-insensitive Regex.|`find . -iregex ".*py"`|

#### B. 📂 By Type

|**Parameter**|**Description**|**Example**|
|---|---|---|
|**`-type f`**|Regular File.|`find . -type f`|
|**`-type d`**|Directory.|`find . -type d`|
|**`-type l`**|Symbolic Link.|`find . -type l`|
|**`-type b`**|Block device.|`find /dev -type b`|
|**`-type c`**|Character device.|`find /dev -type c`|
|**`-type p`**|Named pipe (FIFO).|`find /var -type p`|
|**`-type s`**|Socket.|`find /tmp -type s`|
|**`-empty`**|Empty file or directory.|`find . -type d -empty`|

#### C. ⏳ By Timestamp

_Units: `n` (exactly n), `+n` (older than n), `-n` (newer than n)._

|**Parameter**|**Description**|**Example**|
|---|---|---|
|**`-mtime n`**|Modified _n_ **days** ago.|`find . -mtime -7` (Modified in last 7 days)|
|**`-mmin n`**|Modified _n_ **minutes** ago.|`find . -mmin -60` (Modified in last hour)|
|**`-atime n`**|Accessed _n_ **days** ago.|`find . -atime +30` (Accessed > 30 days ago)|
|**`-amin n`**|Accessed _n_ **minutes** ago.|`find . -amin 5` (Accessed exactly 5 mins ago)|
|**`-ctime n`**|Status changed _n_ **days** ago.|`find . -ctime 0` (Changed today)|
|**`-cmin n`**|Status changed _n_ **minutes** ago.|`find . -cmin -10`|
|**`-newer [file]`**|Modified more recently than `[file]`.|`find . -newer /tmp/marker_file`|

#### D. ⚖️ By Size

_Suffixes: `k` (KiB), `M` (MiB), `G` (GiB)._

|**Parameter**|**Description**|**Example**|
|---|---|---|
|**`-size n`**|Exactly _n_ units.|`find . -size 10M`|
|**`-size +n`**|Larger than _n_.|`find . -size +1G`|
|**`-size -n`**|Smaller than _n_.|`find . -size -500k`|

#### E. 🔐 By Permissions & Ownership

|**Parameter**|**Description**|**Example**|
|---|---|---|
|**`-user`**|Owned by user.|`find . -user jenny`|
|**`-group`**|Owned by group.|`find . -group developers`|
|**`-nouser`**|ID has no user name (orphaned).|`find . -nouser`|
|**`-nogroup`**|ID has no group name.|`find . -nogroup`|
|**`-perm mode`**|Permissions are **exactly** _mode_.|`find . -perm 755`|
|**`-perm -mode`**|**All** these bits are set.|`find . -perm -u+x` (User can exec)|
|**`-perm /mode`**|**Any** of these bits are set.|`find . -perm /u+w,g+w` (Writable by user OR group)|
|**`-readable`**|Readable by current user.|`find . -readable`|
|**`-writable`**|Writable by current user.|`find . -writable`|
|**`-executable`**|Executable by current user.|`find . -executable`|

---

### 5. 🎬 Actions (What to do)

|**Action**|**Description**|**Example**|
|---|---|---|
|**`-print`**|Print path (Default).|`find . -name "*.txt" -print`|
|**`-print0`**|Print path with null-terminator.|`find . -name "*.png" -print0|
|**`-ls`**|List in `ls -dils` format.|`find . -size +10M -ls`|
|**`-delete`**|Delete the file.|`find . -name "*.tmp" -delete`|
|**`-exec ... \;`**|Run command (one per file).|`find . -name "*.sh" -exec chmod +x {} \;`|
|**`-exec ... +`**|Run command (batch files).|`find . -name "*.log" -exec tar -cvf logs.tar {} +`|
|**`-execdir`**|Run command from file's dir.|`find . -name "*.js" -execdir npm test {} \;`|
|**`-ok`**|Ask confirmation before exec.|`find . -user olduser -ok rm {} \;`|
|**`-quit`**|Stop after first match.|`find . -name "needle" -print -quit`|
|**`-prune`**|Exclude/Don't descend.|`find . -path ./node_modules -prune -o -print`|

---

### 6. 🧠 Operators (Logic)

|**Operator**|**Description**|**Example**|
|---|---|---|
|**`( expr )`**|Grouping (Precedence).|`find . \( -name "*.c" -o -name "*.h" \)`|
|**`!`, `-not`**|Invert result.|`find . ! -user root` (Not owned by root)|
|**`-a`, `-and`**|Logical AND (Implicit).|`find . -type f -and -size +10M`|
|**`-o`, `-or`**|Logical OR.|`find . -name "*.jpg" -or -name "*.png"`|
|**`,`**|List (Evaluate both).|`find . -name "*.txt" -print , -name "*.xml" -delete`|

---

### 7. 🖨️ Custom Formatting (`-printf`)

_Use these with the syntax: `find . -printf "format_string"`_

|**Code**|**Output**|**Example Command**|
|---|---|---|
|`%p`|Full path.|`find . -printf "Path: %p\n"`|
|`%f`|Filename only.|`find . -printf "File: %f\n"`|
|`%h`|Directory only.|`find . -printf "Folder: %h\n"`|
|`%s`|Size (bytes).|`find . -printf "%p is %s bytes\n"`|
|`%u`|Username.|`find . -printf "Owner: %u\n"`|
|`%g`|Group name.|`find . -printf "Group: %g\n"`|
|`%m`|Permissions (octal).|`find . -printf "Perms: %m\n"`|
|`%Tc`|Mod time.|`find . -printf "Modified: %Tc\n"`|
