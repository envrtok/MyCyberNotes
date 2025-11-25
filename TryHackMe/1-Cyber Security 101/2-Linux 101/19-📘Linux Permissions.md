## 🔑 Overview and classes

- **Scope:** Permissions control access for files and directories.
- **Classes:** 👤 **Owner (u)**, 👥 **Group (g)**, 🌍 **Others (o)**.
- **Model:** Each class gets a triplet of bits: **r**, **w**, **x**.

---

## 📝 Permission types and meaning

- **Read (r):** 📖 View file contents; list directory entries.
- **Write (w):** ✍️ Modify file; create/rename/delete inside a directory.
- **Execute (x):** 🚀 Run a file; enter/traverse a directory (search permission).

---

## 🔍 Representation and binary ↔ octal mapping

- **Long listing:** `ls -l` shows type + 3 triplets:
    - **Type:** `-` file, `d` directory, `l` symlink, etc.
    - **Triplets:** owner, group, others (e.g., `-rwxr-xr--`).

### 🧮 Complete binary ↔ octal table

|Permission|Binary|Octal|
|---|---|---|
|rwx|111|7|
|rw-|110|6|
|r-x|101|5|
|r--|100|4|
|-wx|011|3|
|-w-|010|2|
|--x|001|1|
|---|000|0|

---

## ⚙️ Changing permissions and ownership

- **chmod (symbolic):**
    - **Add/Remove:** `chmod u+x file`, `chmod go-r file`.
    - **Set exactly:** `chmod u=rwx,g=rx,o= file`.
- **chmod (numeric):**
    - **Octal:** three digits map to u/g/o (e.g., `755`, `640`, `700`).
- **Ownership:**
    - **Change owner:** `chown user file`.
    - **Change group:** `chgrp group file`.

---

## 🛡️ Special bits (setuid, setgid, sticky)

- **Setuid (4xxx):** 👤 Executables run with file owner’s effective UID.
    - **Numeric:** add leading 4 (e.g., `4755`).
    - **Display:** owner triplet shows `s`/`S` (x set → `s`; x unset → `S`).
- **Setgid (2xxx):** 👥 Executables run with file group’s GID; on directories, new files inherit the directory’s group.
    - **Numeric:** add leading 2 (e.g., `2755`).
    - **Display:** group triplet `s`/`S`.
- **Sticky (1xxx):** 📌 On directories (e.g., `/tmp`), only the file owner or root can delete/rename inside.
    - **Numeric:** add leading 1 (e.g., `1777`).
    - **Display:** others triplet `t`/`T`.

---

## 🚀 Quick examples and formula mini sheet

- **Common modes:**
    - **Code:** `chmod 644 file.txt`
    - **Meaning:** Owner rw-, Group r--, Others r--.
- **Private script:**
    - **Code:** `chmod 700 script.sh`
    - **Meaning:** Owner rwx, Group ---, Others ---.
- **Executable for all, writable only by owner:**
    - **Code:** `chmod 755 app`
    - **Meaning:** u=rwx, g=rx, o=rx.
- **Shared write dir with group inheritance:**
    - **Code:** `chmod 2775 shared/`
    - **Meaning:** sgid on, u=rwx, g=rwx, o=rx.
- **World-writable temp dir with sticky:**
    - **Code:** `chmod 1777 /tmp-like/`
    - **Meaning:** sticky on, u=rwx, g=rwx, o=rwx (but protected deletes).

### ⚡ Formula mini sheet

- **Triplet → octal:** rwx=7, rw-=6, r-x=5, r--=4, -wx=3, -w-=2, --x=1, ---=0.
- **Mode pattern:** special u g o (e.g., 1 7 7 7 → sticky + rwx/rwx/rwx).
- **Symbolic ops:** `u/g/o` + `+ - =` + `r w x` (e.g., `g+w`, `o-rx`, `u=rx`).
- **Directory must-haves:** write needs execute to create/delete; execute without read allows traversal by name.
