# MySQL Practice Session — `acharya` Database

## Environment
- **OS:** Windows 10 (Build 26200.7922)
- **MySQL Version:** 8.0.45 Community Server (GPL)

---

## 1. Connecting & Exploring Databases

```sql
mysql -u root -p

SHOW DATABASES;
```

**Output:**
```
+--------------------+
| Database           |
+--------------------+
| acharya            |
| clg                |
| college            |
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
```

```sql
USE acharya;
SHOW TABLES;
```

**Output:**
```
+-------------------+
| Tables_in_acharya |
+-------------------+
| employee          |
+-------------------+
```

---

## 2. Viewing the `employee` Table

```sql
SELECT * FROM employee;
```

**Output:**
```
+--------+----------+------------+---------+------------+-------+
| emp_no | e_name   | manager_no | sal     | commission | job   |
+--------+----------+------------+---------+------------+-------+
|      1 | Farhan   |        101 | 1000000 |        123 | SDE-2 |
|      2 | Mohammed |        102 | 2000000 |        124 | SDE-2 |
|      3 | Red Eye  |        103 | 3000000 |        125 | SDE-2 |
+--------+----------+------------+---------+------------+-------+
```

```sql
DESC employee;
```

**Output:**
```
+------------+-------------+------+-----+---------+-------+
| Field      | Type        | Null | Key | Default | Extra |
+------------+-------------+------+-----+---------+-------+
| emp_no     | int         | YES  |     | NULL    |       |
| e_name     | varchar(10) | YES  |     | NULL    |       |
| manager_no | int         | YES  |     | NULL    |       |
| sal        | mediumtext  | YES  |     | NULL    |       |
| commission | int         | YES  |     | NULL    |       |
| job        | varchar(10) | YES  |     | NULL    |       |
+------------+-------------+------+-----+---------+-------+
```

---

## 3. Adding a PRIMARY KEY Constraint

> **Error (wrong column name):**
> ```sql
> ALTER TABLE employee ADD CONSTRAINT PRIMARY KEY(empno);
> -- ERROR 1072: Key column 'empno' doesn't exist in table
> ```

**Correct query:**
```sql
ALTER TABLE employee ADD CONSTRAINT PRIMARY KEY(emp_no);
```

After applying, `emp_no` is now `NOT NULL` with `PRI` key.

---

## 4. Inserting Records

### Duplicate Primary Key Error
```sql
INSERT INTO employee VALUES (003, "am", 106, 121234, 2446, "SDE-1");
-- ERROR 1062: Duplicate entry '3' for key 'employee.PRIMARY'
```

### NULL Primary Key Error
```sql
INSERT INTO employee VALUES (null, "am", 106, 121234, 2446, "SDE-1");
-- ERROR 1048: Column 'emp_no' cannot be null
```

### Successful Insert
```sql
INSERT INTO employee VALUES (4, "null", 106, 121234, 2446, "SDE-1");
-- Query OK
```

---

## 5. Adding NOT NULL Constraint on `e_name`

> **Error (wrong column name):**
> ```sql
> ALTER TABLE employee MODIFY ename VARCHAR(10) NOT NULL;
> -- ERROR 1054: Unknown column 'ename' in 'employee'
> ```

**Correct query:**
```sql
ALTER TABLE employee MODIFY e_name VARCHAR(10) NOT NULL;
```

### NULL Name Error (after constraint)
```sql
INSERT INTO employee VALUES (8, null, 106, 121234, 2446, 'SDE-1');
-- ERROR 1048: Column 'e_name' cannot be null
```

---

## 6. TCL — Transaction Control (autocommit & ROLLBACK)

### Autocommit Typo Errors
```sql
SET autcommit = 1;   -- ERROR: Unknown system variable 'autcommit'
SET aut0commit = 1;  -- ERROR: Unknown system variable 'aut0commit'
SET autocommit = 1;  -- Query OK
```

---

### Case 1: ROLLBACK with `autocommit = 0` ✅ (Works)

```sql
SET autocommit = 0;

INSERT INTO employee VALUES (9, 'ram', 106, 121234, 2446, 'SDE-1');
-- Row temporarily inserted (visible in SELECT)

ROLLBACK;
-- Row removed — insert was undone
```

**Key point:** When `autocommit = 0`, transactions are not auto-committed, so `ROLLBACK` works as expected.

---

### Case 2: ROLLBACK with `autocommit = 1` ❌ (Does NOT work)

```sql
SET autocommit = 1;

INSERT INTO employee VALUES (9, 'ram', 106, 121234, 2446, 'SDE-1');
-- Row permanently inserted (auto-committed immediately)

ROLLBACK;
-- No effect — row still present
```

**Key point:** When `autocommit = 1`, each statement is committed immediately. `ROLLBACK` has no effect.

---

## 7. Final Table State

```sql
SELECT * FROM employee;
```

```
+--------+----------+------------+---------+------------+-------+
| emp_no | e_name   | manager_no | sal     | commission | job   |
+--------+----------+------------+---------+------------+-------+
|      1 | Farhan   |        101 | 1000000 |        123 | SDE-2 |
|      2 | Mohammed |        102 | 2000000 |        124 | SDE-2 |
|      3 | Red Eye  |        103 | 3000000 |        125 | SDE-2 |
|      4 | null     |        106 | 121234  |       2446 | SDE-1 |
|      5 | null     |        106 | 121234  |       2446 | SDE-1 |
|      6 | null     |        106 | 121234  |       2446 | SDE-1 |
|      7 | null     |        106 | 121234  |       2446 | SDE-1 |
|      9 | ram      |        106 | 121234  |       2446 | SDE-1 |
+--------+----------+------------+---------+------------+-------+
```

---

## Summary of Concepts Covered

| Concept | Command Used |
|---|---|
| View databases/tables | `SHOW DATABASES`, `SHOW TABLES` |
| Table structure | `DESC employee` |
| Add PRIMARY KEY | `ALTER TABLE ... ADD CONSTRAINT PRIMARY KEY` |
| Add NOT NULL | `ALTER TABLE ... MODIFY ... NOT NULL` |
| Insert records | `INSERT INTO ... VALUES (...)` |
| Transaction control | `SET autocommit`, `ROLLBACK` |
| Common errors | Duplicate PK, NULL constraint, wrong column name |
