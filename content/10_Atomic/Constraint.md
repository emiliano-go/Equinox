---
tags:
  - definition
  - atomic
created: 2026-04-28
---

# Constraint

A **constraint** is a **rule enforced by the database** that restricts the data that can be stored.

It ensures
- Correctness
- Consistency
- Integrity

##### In Relational Databases
A constraint is applied to a table or column to control **what values are allowed**.

### Common types of constraints

##### NOT NULL
Value cannot be missing

```sql
name TEXT NOT NULL
```

##### UNIQUE
No duplicate values allowed

```sql
email TEXT UNIQUE
```

##### PRIMARY KEY
- Unique + Not null
- Identifies each tuple

##### FOREIGN KEY
- Must match a value in another table (usually the Primary Key)
- Enforces Relationships

##### CHECK
Custom condition.

```sql
age INT CHECK (age >= 0)
```

##### DEFAULT
Provides a value if none is given.

```sql
status TEXT DEFAULT 'active'
```