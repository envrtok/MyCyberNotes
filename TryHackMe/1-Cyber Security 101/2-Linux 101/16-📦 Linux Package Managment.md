## 📦 Introducing Packages & Software Repositories

- Developers submit software to an **apt repository**.
- Once approved, their programs become available to the community.
- This highlights two strengths of Linux:
    - **Accessibility for users**
    - **Open-source collaboration**

On Ubuntu 20.04, repository files act as the **gateway/registry** for installed software.

Operating system vendors maintain their own repositories, but you can also add **community repositories** to extend functionality.

- Use `add-apt-repository` or manually add another provider.
- Some vendors host repositories closer to your geographical location for faster access.

---

## ⚙️ Managing Repositories (Adding & Removing)

### Using `apt`

- The `apt` command is the core of Ubuntu’s package management.
- It allows you to **install, update, and remove software**.
- Unlike manual installers like `dpkg`, apt ensures that repositories are checked for updates whenever you update your system.

---

## ✍️ Example: Adding Sublime Text Repository

Sublime Text is not included in Ubuntu’s default repositories, so we’ll add it manually.

### Step 1: Add the GPG Key

GPG (GNU Privacy Guard) keys verify the integrity of software.

```bash
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
```

### Step 2: Add the Repository

It’s best practice to create a separate file for each third-party repository.

1. Create a file:
    
    ```bash
    sudo nano /etc/apt/sources.list.d/sublime-text.list
    ```
    
2. Add the Sublime Text repository information inside this file.
3. Save and exit.

### Step 3: Update apt

```bash
sudo apt update
```

### Step 4: Install Sublime Text

```bash
sudo apt install sublime-text
```

---

## 🗑 Removing Repositories & Packages

- Remove a repository:
    
    ```bash
    add-apt-repository --remove ppa:PPA_Name/ppa
    ```
    
    or manually delete the file in `/etc/apt/sources.list.d/`.
    
- Remove a package:
    
    ```bash
    sudo apt remove sublime-text
    ```