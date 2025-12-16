## 📂 Core Concepts

- **Database** → Holds multiple tables.
- **Table** → A structured set of data inside a database.
- **Column** → Defines the type of data (e.g., id, name, age).
- **Row** → A single record inside a table.

---

## 🔑 Connecting

```bash
mysql -h <host_ip> -P 3306 -u <user> -p
```

- `-h` → Server IP/hostname
- `-P` → Port (default 3306)
- `-u` → Username
- `-p` → Prompts for password

Once connected, you’ll see the `mysql>` prompt. End every SQL command with `;`.

---

## 📂 Database Commands

```sql
SHOW DATABASES;      -- List all databases
USE <db_name>;       -- Switch to a database
```

💻 **Shell shortcut (no interactive prompt):**

```bash
mysql -e "SHOW DATABASES;"
mysql -D <db_name> -e "USE <db_name>;"
```

---

## 📑 Table Commands

```sql
SHOW TABLES;         -- List tables in the current database
DESCRIBE <table>;    -- Show table structure (columns)
```

💻 **Shell shortcut:**

```bash
mysql -D <db_name> -e "SHOW TABLES;"
mysql -D <db_name> -e "DESCRIBE users;"
```

---

## 📊 Data Commands

```sql
SELECT * FROM <table>;              -- Get all rows
SELECT name FROM users;             -- Get specific column
SELECT * FROM users WHERE id=1;     -- Filtered query
SELECT * FROM users LIMIT 5;        -- Limit results

INSERT INTO users VALUES (1, 'Enver', 25);  -- Add a row
UPDATE users SET age=26 WHERE id=1;         -- Update a row
DELETE FROM users WHERE id=1;               -- Delete a row
```

💻 **Shell shortcut:**

```bash
mysql -D <db_name> -e "SELECT * FROM users LIMIT 5;"
mysql -D <db_name> -e "INSERT INTO users VALUES (1, 'Enver', 25);"
mysql -D <db_name> -e "UPDATE users SET age=26 WHERE id=1;"
mysql -D <db_name> -e "DELETE FROM users WHERE id=1;"
```