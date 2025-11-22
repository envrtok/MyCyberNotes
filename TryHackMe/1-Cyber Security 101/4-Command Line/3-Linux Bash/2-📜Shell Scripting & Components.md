Shell scripting = **automation of repetitive tasks** by combining commands into a single file.  
Instead of typing commands one by one, you execute the script → all commands run automatically.

---

## 🛠️ Basics of Shell Scripting

- Works in **all shells** (Bash, Zsh, Fish, etc.)
- Scripts are plain text files with `.sh` extension
- Must start with **shebang (`#!`)** → defines interpreter (e.g., `#!/bin/bash`)
- Example:
    
    ```bash
    #!/bin/bash
    echo "Hello World"
    ```
    

---

## 📂 Creating & Running a Script

1. Create file: `nano first_script.sh`
2. Add shebang + commands
3. Save (`CTRL+X`, `Y`, `ENTER`)
4. Give execution permission: `chmod +x first_script.sh`
5. Run: `./first_script.sh`

⚡ Note: `./` tells shell to run file in **current directory** (not PATH).

---

# 🧩 Script Components

## 🔑 Variables

- Store values (e.g., names, paths, URLs)
- Example:
    
    ```bash
    #!/bin/bash
    echo "Hey, what’s your name?"
    read name
    echo "Welcome, $name"
    ```
    
- `read` → takes input
- `$variable` → expands stored value

---

## 🔁 Loops

- Repeat tasks automatically
- Example: print numbers 1–10
    
    ```bash
    #!/bin/bash
    for i in {1..10}; do
      echo $i
    done
    ```
    
- `do` → start loop body
- `done` → end loop body

---

## ⚖️ Conditional Statements

- Execute code **only if condition is true**
- Example: authorized user check
    
    ```bash
    #!/bin/bash
    echo "Enter your name:"
    read name
    if [ "$name" = "Stewart" ]; then
        echo "Welcome Stewart! Secret: THM_Script"
    else
        echo "Sorry! Not authorized."
    fi
    ```
    
- `if … then … else … fi` → structure

---

## 📝 Comments

- Improve readability, don’t affect execution
- Written with `#`
- Example:
    
    ```bash
    # Asking user for input
    read name
    # Checking authorization
    if [ "$name" = "Stewart" ]; then
        echo "Secret unlocked"
    fi
    ```
    

---

# 📊 Quick Reference Table

|🧩 Component|⚡ Purpose|🖊️ Example|
|---|---|---|
|**Shebang**|Defines interpreter|`#!/bin/bash`|
|**Variable**|Store/reuse values|`name="John"`|
|**Loop**|Repeat tasks|`for i in {1..10}`|
|**Condition**|Branch logic|`if [ "$x" = "y" ]`|
|**Comment**|Explain code|`# This is a note`|

---

# 🎯 Key Takeaways

- Shell scripts = **automation + efficiency**
- Components: **variables, loops, conditionals, comments**
- Always: **shebang + execution permission**
- Best practice: add **comments in complex areas** for clarity