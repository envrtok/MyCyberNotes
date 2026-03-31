**Local File Inclusion (LFI)** is a security vulnerability that allows an attacker to read local files on a server (e.g., `/etc/passwd` on Linux systems). It typically occurs when web applications use functions like `include`, `require`, or `include_once` in PHP without properly validating user input.

Below are the fundamental LFI scenarios and the techniques used to exploit them:

### 1. Unrestricted Inclusion

The developer includes user input directly into the function without specifying any directory or extension.

- **Vulnerable Code:** `include($_GET["lang"]);`
    
- **Obstacle:** None. Any file can be accessed starting from the root directory.
    
- **Exploit (Payload):** `?lang=/etc/passwd` _(Using an absolute path)_
    

### 2. Directory Restriction (Directory Prefix)

The developer forces the application to look for files only within a specific folder (e.g., `languages/`).

- **Vulnerable Code:** `include("languages/" . $_GET['lang']);`
    
- **Obstacle:** The system looks for the input inside the `languages/` folder.
    
- **Exploit (Payload):** `?lang=../../../../etc/passwd` _(Path Traversal)_
    
- **Logic:** Use `../` to navigate out of the restricted directory until you reach the root directory (`/`) to access the target file.
    

### 3. Mandatory File Extension (Suffix)

The developer automatically appends an extension like `.php` to the user's input.

- **Vulnerable Code:** `include("languages/". $_GET['lang'] .".php");`
    
- **Obstacle:** If you request `/etc/passwd`, the system looks for a non-existent file: `/etc/passwd.php`.
    
- **Exploit (Payload):** `?lang=../../../../etc/passwd%00` _(Null Byte Bypass)_
    
- **Logic:** `%00` (Null Byte) signals the end of a string in programming. When the system encounters it, it ignores everything that follows (like `.php`). _(Note: This is fixed in PHP 5.3.4 and above.)_
    

### 4. Keyword Filtering (Blacklisting/WAF)

The developer blacklists sensitive file paths like `/etc/passwd` to prevent unauthorized access.

- **Obstacle:** The application blocks the request if the string `/etc/passwd` is detected.
    
- **Exploit (Payload):** `?lang=../../../../etc/passwd/.` _(Current Directory Trick)_
    
- **Logic:** A single dot (`.`) represents the "current directory" in file systems. Appending `/.` to the path does not change the file location but bypasses the filter because the system no longer sees the "exact" forbidden string it was looking for.
    

### 5. Inadequate Cleaning (Recursive Filter Bypass)

The developer attempts to remove the `../` (path traversal) sequence by replacing it with an empty string (`""`).

- **Obstacle:** The `../` sequence is stripped from the input.
    
- **Exploit (Payload):** `?lang=....//....//....//....//etc/passwd`
    
- **Logic:** Filters often run only once. When the system removes the inner `../`, the remaining characters shift and combine to form a new, valid `../` sequence.
    

### 6. Mandatory Prefix Requirement

The application requires the input to start with a specific directory name (e.g., `languages/`).

- **Obstacle:** If the input does not start with the required prefix, the request is rejected.
    
- **Exploit (Payload):** `?lang=languages/../../../../etc/passwd`
    
- **Logic:** You provide the required prefix to satisfy the validation, then immediately use `../` to navigate out of that folder and reach the target file.
    

---

### ⚡ Quick Summary Cheat Sheet

|**Scenario / Obstacle**|**Situation**|**Bypass Technique / Payload**|
|---|---|---|
|**No Restriction**|Can access files directly.|`/etc/passwd`|
|**Directory Restriction**|Restricted to a specific folder.|`../../../../etc/passwd`|
|**Mandatory Extension**|`.php` is appended to input.|`../../../../etc/passwd%00`|
|**Keyword Filter**|`/etc/passwd` is blacklisted.|`../../../../etc/passwd/.`|
|**Character Stripping**|`../` is deleted by the filter.|`....//....//etc/passwd`|
|**Mandatory Prefix**|Must start with a specific folder.|`folder/../../../../etc/passwd`|
