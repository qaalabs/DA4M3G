---
title: Types of SQL
---

# SQL is not one language

SQL is split into sub-languages - each group of commands has a different job.

| Type | Full name | Job |
|------|-----------|-----|
| DDL | Data Definition Language | Define structure |
| DML | Data Manipulation Language | Change data |
| DQL | Data Query Language | Read data |
| DCL | Data Control Language | Control access |
| TCL | Transaction Control Language | Manage transactions |

---

# DDL - Data Definition Language

**Defines and changes the structure of objects.**

```sql
CREATE TABLE orders (id INT, amount DECIMAL);
ALTER TABLE orders ADD COLUMN status VARCHAR(20);
DROP TABLE orders;
TRUNCATE TABLE orders;
```

- Changes the schema, not the data
- Usually auto-commits (can't be rolled back in most databases)

---

# DML - Data Manipulation Language

**Adds, changes, or removes rows.**

```sql
INSERT INTO orders (id, amount) VALUES (1, 99.99);
UPDATE orders SET status = 'shipped' WHERE id = 1;
DELETE FROM orders WHERE id = 1;
```

- Operates on rows, not structure
- Can be wrapped in a transaction and rolled back

---

# DQL - Data Query Language

**Reads data — the most-used type.**

```sql
SELECT id, amount
FROM orders
WHERE status = 'shipped'
ORDER BY amount DESC;
```

- `SELECT` is the only DQL command
- Sometimes grouped under DML, but the distinction is useful:
  DQL reads, DML writes

---

# DCL - Data Control Language

**Controls who can do what.**

```sql
GRANT SELECT ON orders TO analyst_role;
REVOKE DELETE ON orders FROM intern_role;
```

- Manages permissions on database objects
- Typically run by a DBA or platform engineer, not application code

---

# TCL - Transaction Control Language

**Wraps DML in an all-or-nothing unit.**

```sql
BEGIN;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;
COMMIT;
-- or ROLLBACK; to undo both updates
```

- `COMMIT` - save the changes permanently
- `ROLLBACK` - undo everything since `BEGIN`
- `SAVEPOINT` - set a named checkpoint to roll back to

---

# Summary

| Type | Commands                      | Affects |
|------|-------------------------------|---------|
| DDL  | CREATE, ALTER, DROP, TRUNCATE | Schema |
| DML  | INSERT, UPDATE, DELETE        | Rows |
| DQL  | SELECT                        | Reads (no change)|
| DCL  | GRANT, REVOKE                 | Permissions   |
| TCL  | BEGIN, COMMIT, ROLLBACK       | Transactions |

