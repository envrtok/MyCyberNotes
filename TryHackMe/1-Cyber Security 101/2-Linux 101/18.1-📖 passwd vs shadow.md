## 🔹 `/etc/passwd`

- **Purpose:** Holds basic information about all user accounts.
- **Contents:**
    - Username
    - User ID (UID)
    - Group ID (GID)
    - Home directory path
    - Default login shell
- **Password field:** Usually contains an `x` or `*` as a placeholder, meaning the actual password hash is stored in `/etc/shadow`.
- **Permissions:** World‑readable, because system processes need to know user IDs and shells.

👉 Example line:

```
enver:x:1001:1001:Enver,,,:/home/enver:/bin/bash
```

---

## 🔹 `/etc/shadow`

- **Purpose:** Stores encrypted (hashed) passwords and password aging information.
- **Contents:**
    - Username
    - Hashed password
    - Password expiration and aging details (last change date, min/max days, etc.)
- **Permissions:** Only root can read this file, protecting password hashes from regular users.

👉 Example line:

```
enver:$6$abc123$kjsdfhksjdfhksjdfhksjdfhksjdfhksjdfhksjdfhksjdfh:19234:0:99999:7:::
```

Here `$6$` indicates SHA‑512 hashing.

---

## 🔹 Key Differences

|Feature|`/etc/passwd`|`/etc/shadow`|
|---|---|---|
|**Purpose**|User account info|Password hashes + policies|
|**Password field**|Placeholder (`x` or `*`)|Actual hashed password|
|**Access**|World‑readable|Root‑only|
|**Security**|Low (no hashes inside)|High (hashes protected)|

---

⚡ **Summary:**

- `/etc/passwd` = _who the users are_.
- `/etc/shadow` = _their password hashes and rules_.
- This separation enhances security by keeping sensitive data out of a world‑readable file.