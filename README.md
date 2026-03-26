# 📚 DBMS — Database Management Systems
### VTU | 4th Semester | Computer Science & Engineering

---

## 📋 Subject Overview

| Detail | Info |
|---|---|
| **Subject Code** | 21CS42 (CBCS 2022 Scheme) |
| **Semester** | 4th Sem, B.E. CSE |
| **Credits** | 3 |
| **Contact Hours** | 3L + 0T + 0P per week |
| **University** | Visvesvaraya Technological University (VTU) |

---

## 📖 Syllabus Modules

### Module 1 — Introduction to Databases
- Purpose of Database Systems
- View of Data: Data Models, Schemas, Instances
- Database Languages: DDL, DML, DCL, TCL
- Database Users and Administrators
- Transaction Management
- Database System Structure

### Module 2 — Entity-Relationship (ER) Model
- Basic Concepts: Entities, Attributes, Relationships
- Constraints: Mapping Cardinalities, Participation Constraints
- Keys: Super Key, Candidate Key, Primary Key
- ER Diagram Notation
- Weak Entity Sets
- Extended ER Features: Generalization, Specialization, Aggregation

### Module 3 — Relational Model & Relational Algebra
- Structure of Relational Databases
- Relational Algebra Operations:
  - Select (σ), Project (π), Union (∪), Set Difference (−), Cartesian Product (×)
  - Join, Rename (ρ)
  - Aggregate Functions
- Relational Database Design
- Introduction to SQL: DDL, DML, Integrity Constraints
- Advanced SQL: Nested Queries, Views, Triggers

### Module 4 — Normalization & Functional Dependencies
- Functional Dependencies
- Armstrong's Axioms
- Normal Forms: 1NF, 2NF, 3NF, BCNF
- Decomposition: Lossless Join, Dependency Preservation
- 4NF, 5NF (overview)
- Multivalued Dependencies

### Module 5 — Transactions, Concurrency & Recovery
- Transaction Concepts: ACID Properties
- Transaction States
- Concurrency Control:
  - Lock-based Protocols (Shared & Exclusive Locks)
  - Two-Phase Locking (2PL)
  - Timestamp-based Protocols
  - Deadlock Handling
- Recovery System:
  - Log-based Recovery
  - Checkpoints
  - ARIES Algorithm (overview)

---

## 🗂️ Recommended Textbooks

| # | Book | Author(s) | Publisher |
|---|---|---|---|
| 1 | *Database System Concepts* (7th Ed.) | Silberschatz, Korth, Sudarshan | McGraw-Hill |
| 2 | *Fundamentals of Database Systems* (7th Ed.) | Elmasri & Navathe | Pearson |
| 3 | *An Introduction to Database Systems* | C.J. Date | Pearson |

---

## 🛠️ Tools & Software

| Tool | Purpose |
|---|---|
| **MySQL / PostgreSQL** | Practice SQL queries |
| **Oracle XE** | Industry-standard RDBMS |
| **SQLite** | Lightweight DB for quick testing |
| **MySQL Workbench** | GUI for DB design and querying |
| **DB Browser for SQLite** | Lightweight GUI tool |
| **draw.io / Lucidchart** | Draw ER Diagrams |

---

## 📂 Repository Structure (Suggested)

```
DBMS-4thSem-VTU/
│
├── notes/
│   ├── module1_introduction.pdf
│   ├── module2_er_model.pdf
│   ├── module3_relational_algebra_sql.pdf
│   ├── module4_normalization.pdf
│   └── module5_transactions_recovery.pdf
│
├── sql-practicals/
│   ├── ddl_commands.sql
│   ├── dml_commands.sql
│   ├── joins_practice.sql
│   ├── subqueries.sql
│   ├── views_triggers.sql
│   └── normalization_examples.sql
│
├── er-diagrams/
│   ├── university_db.png
│   ├── hospital_db.png
│   └── banking_db.png
│
├── question-papers/
│   ├── 2022_dec_qp.pdf
│   ├── 2023_june_qp.pdf
│   └── model_qp.pdf
│
└── README.md
```

---

## 🧠 Key Concepts Quick Reference

### ACID Properties
- **A**tomicity — All or nothing
- **C**onsistency — DB remains in a valid state
- **I**solation — Transactions don't interfere
- **D**urability — Committed data persists

### Normal Forms Cheatsheet
| Normal Form | Rule |
|---|---|
| **1NF** | All attributes are atomic (no repeating groups) |
| **2NF** | 1NF + No partial dependency on primary key |
| **3NF** | 2NF + No transitive dependency |
| **BCNF** | Every determinant is a candidate key |

### ER to Relational Mapping (Quick Steps)
1. Map strong entity sets → relations
2. Map weak entity sets → relations (include owner's PK)
3. Map binary 1:1, 1:N, M:N relationships
4. Map multivalued attributes → separate relation
5. Map n-ary relationships

---

## 📝 Previous Year Important Questions

- Explain the difference between a schema and an instance.
- Draw and explain the ER diagram for a University database.
- Write relational algebra expressions for given queries.
- Normalize a given relation to 3NF / BCNF with proof.
- Explain Two-Phase Locking protocol with an example.
- What are the ACID properties? Explain with examples.
- Differentiate between DDL and DML.
- Explain timestamp-based concurrency control.

---

## 🔗 Useful Resources

- [VTU eLearning Portal](https://vtu.ac.in)
- [NPTEL DBMS Course (IIT Madras)](https://nptel.ac.in)
- [W3Schools SQL Tutorial](https://www.w3schools.com/sql/)
- [SQLZoo — Interactive SQL Practice](https://sqlzoo.net)
- [GeeksForGeeks DBMS](https://www.geeksforgeeks.org/dbms/)
- [Studocu VTU Notes](https://www.studocu.com)

---

## ✅ Study Tips

1. **Understand ER diagrams** — practice converting real-world scenarios.
2. **Master Relational Algebra** before jumping to SQL.
3. **Normalization** — practice plenty of examples; this is a guaranteed exam topic.
4. **SQL practicals** — hands-on practice with MySQL is essential.
5. **Solve 5 years of VTU question papers** for pattern recognition.
6. **ACID + Concurrency** — understand conceptually with diagrams.

---

> 💡 *"Data is a precious thing and will last longer than the systems themselves."* — Tim Berners-Lee

---

*README maintained for VTU 4th Sem DBMS | 2021 Scheme | CSE/ISE*
