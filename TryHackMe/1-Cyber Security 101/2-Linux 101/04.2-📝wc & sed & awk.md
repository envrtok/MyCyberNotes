# 🧮 **wc Command (Word Count)**

The **wc (word count)** command helps you quickly determine **how large a file is** or **how much data it contains**.

### ✔️ Example

```
root@hackerbox:~$ wc /etc/passwd
46   67 2544 /etc/passwd
```

The output represents:

|Value|Meaning|
|---|---|
|**46**|Number of lines 📄|
|**67**|Number of words 📝|
|**2544**|Number of characters 🔡|
|**/etc/passwd**|File path 📁|

### 🔧 Useful wc Options

|Option|Description|
|---|---|
|**-l**|Show only the number of lines|
|**-w**|Show only the number of words|
|**-c**|Show the number of bytes|
|**-m**|Show the number of characters (useful for multi-byte encodings)|

### ✔️ Example — Count total lines in Apache access logs

```
root@hackerbox:~$ wc -l /var/log/apache2/access.log
54230 /var/log/apache2/access.log
```

This output shows that the log file contains **54,230 lines**.

---

# ✂️ **sed Command (Stream Editor)**

The **sed** command is a powerful tool used to **process, modify, replace, insert, or delete text**.  
It is commonly used for text transformation and filtering.

### 📘 Example

```
root@hackerbox:~$ cat names.txt
Alice
Charlie
Bob

root@hackerbox:~$ sed 's/Alice/George/' names.txt
George
Charlie
Bob
```

In this example, **sed** replaces the name _Alice_ with _George_.  
👉 Note: This **does not modify the file itself**; it only prints the modified output to the terminal.

---

# 🧠 **awk Command**

The **awk** command is designed for **text and data processing**.  
It is especially powerful when working with **column-based** or **structured** text.

`awk` reads files **line by line**, splits each line into **fields (columns)**, and performs actions based on patterns or conditions.

### 📘 Example

```
root@hackerbox:~$ cat names.txt
John Doe
Emily Clark
Alex Turner

root@hackerbox:~$ awk '{print $1}' names.txt
John
Emily
Alex
```

Here’s what happens:

- awk reads each line
    
- Splits it into fields based on spaces
    
- `{print $1}` tells awk to print the **first field** (the first name)