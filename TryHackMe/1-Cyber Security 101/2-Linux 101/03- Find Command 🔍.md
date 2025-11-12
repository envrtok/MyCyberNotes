The `find` command is used for finding files by filtering.

*   `*` means "everything." It can be used with all parameters.
*   `2>/dev/null` blocks error messages. 🚫

---

### **Common Usage & Parameters** ⚙️

#### **1. Basic Search by Name** 📛
**Command:** `find <path> -name <name>`

*   **`<path>`**: The directory to search in. It can be a path or:
    *   `.` : Current path 📁
    *   `..` : Parent path ↩️
    *   `/` : Whole system 🖥️
*   **`-name`**: Filters by the exact file name.

**Examples:**
*   `find ../myfolder/* -name passwords.txt`
*   `find . -name \*.txt 2>/dev/null`

#### **2. Filter by File Type & Check Content** 📄
**Command:** `-type f -exec file {} \;`

*   Finds which files are human-readable. 👀

#### **3. Filter by Size** 📏
**Command:** `-size <size><unit>`

*   Filters by a given byte value. The units are:
    *   `c` : byte 🔹
    *   `k` : kilobyte 🔸
    *   `M` : megabyte 🟨
    *   `G` : gigabyte 🟧

#### **4. Filter by User and Group** 👥
*   **`-user <user>`**: Filters files by owner. 👨‍💼
*   **`-group <group>`**: Filters files by group. 🏢