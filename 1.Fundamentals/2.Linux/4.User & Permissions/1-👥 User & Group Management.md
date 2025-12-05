# 1-👤 User Management in Linux

User management in Linux is essential for **system security** and **efficient resource sharing**. In this section, we’ll focus on how to create, manage, and delete users in Linux.

---

## 🔎 What is a User in Linux?

In Linux systems, a **user** is an individual or entity that logs into the system to perform tasks. Managing users is critical for secure access control, resource allocation, and overall system administration.

Each user is associated with a **user account**, which defines their identity and privileges. A user account typically includes:

- **Username**
- **UID (User ID)**
- **GID (Group ID)**
- **Home directory**
- **Default shell**
- **Password**

Every account has unique values for these properties.

---

## 👥 Types of Users

Linux supports two main types of users:

- **System users** → Created during installation, used to run system services and applications.
- **Normal users** → Created by administrators, with access depending on assigned permissions.

---

## ➕ Creating a User

To create a user, use the `useradd` command. For example, to create a user named **John**:

```bash
root@hackerbox:~$ useradd -u 1002 -d /home/john -s /bin/bash john
```

This creates a user account with:

- UID = **1002**
- Home directory = **/home/john**
- Default shell = **/bin/bash**

You can verify the account with:

```bash
root@hackerbox:~$ id john
uid=1002(john) gid=1002(john) groups=1002(john)
```

---

## ⚙️ User Account Properties

Linux user accounts have several key attributes:

- **Username** → Unique identifier (e.g., `john`)
- **UID & GID** → Numeric IDs for the user and their primary group (e.g., UID=1002, GID=1002)
- **Home Directory** → Personal storage location (e.g., `/home/john`)
- **Default Shell** → Command interpreter used at login (e.g., `/bin/bash`)
- **Password** → Required for authentication
- **Group Membership** → Defines access to system resources and files

All registered users are listed in the `/etc/passwd` file:

```bash
root@hackerbox:~$ cat /etc/passwd
root:x:0:0:System Administrator:/root:/bin/bash
john:x:1002:1002:John Doe:/home/johndoe:/bin/bash
```

### `/etc/passwd` Format

|Field|Description|
|---|---|
|`john`|Username|
|`x`|Placeholder for password (actual password stored in `/etc/shadow`)|
|`1002`|UID (User ID)|
|`1002`|GID (Group ID)|
|`,,,`|GECOS field (optional info like full name or contact details)|
|`/home/john`|Home directory|
|`/bin/bash`|Default shell|

---

## 🔑 Changing a User Password

Passwords can be updated with the `passwd` command:

```bash
root@hackerbox:~$ sudo passwd john
```

You’ll be prompted to enter a new password. For security reasons, the characters you type won’t appear on the screen.

---

## ❌ Deleting a User

To remove a user and their files, use `userdel`:

```bash
root@hackerbox:~$ sudo userdel john
```

This deletes John’s account, home directory, and all files owned by him.

---
# 2-👥 Group Management in Linux

In Linux, **group management** is just as important as user management. Groups allow administrators to assign the same access rights and permissions to multiple users at once. This makes it easier to control resources and manage access across the system.

---

## 🔎 What is a Group in Linux?

A **group** in Linux is a collection of users who share certain permissions and access rights. Groups simplify file system access control and make user management more efficient.

---

## ➕ Creating a Group

To create a new group, use the `groupadd` command. For example, to create a group named **development**:

```bash
root@hackerbox:~$ sudo groupadd development
```

Groups are stored in the `/etc/group` file. You can view them with:

```bash
root@hackerbox:~$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:
tty:x:5:
disk:x:6:
...
development:x:1004:
```

Since `/etc/group` may contain many entries, you can filter for a specific group using `grep`:

```bash
root@hackerbox:~$ cat /etc/group | grep development
development:x:1004:
```

---

## 👤 Adding a User to a Group

To add a user to an existing group, use the `usermod` command with the `-aG` option.

- `-aG` ensures the user is added to the new group **without losing existing group memberships**.

Example: Add user **john** to the **development** group:

```bash
root@hackerbox:~$ sudo usermod -aG development john
```

---

## ❌ Deleting a Group

If a group is no longer needed, remove it with the `groupdel` command:

```bash
root@hackerbox:~$ sudo groupdel development
```

This deletes the **development** group from the system.