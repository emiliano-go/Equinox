---
tags:
  - database
  - concept
  - system-architecture
  - databases
  - io
created: 2026-04-28
---

# Primary Key

A **Primary Key** is a [[Constraint]] that enforces:
1. Uniqueness
2. Non-nullability
3. Entity Identity

#### Internal behavior
When you define a PK, most databases:
- Create a **unique index automatically**
- Use it as the **main access path** to rows

In some systems (like InnoDB in MySQL), the table is physically **clustered by the PK**. This means the data is stored **ordered by the PK**.

#### Types of PKs
##### Natural Key
Comes from real data.
- `email`, `DNI`

> Risk: Can change

##### Surrogate Key
Artificial key. No real work meaning, generated at creation.
- `id`

##### Composite Key
With multiple attributes. 

```sql
PRIMARY KEY (student_id, course_id)
```

Used in **Junction tables**.

### Design rules

- Keep it **small** (affects all indexes)
- Keep it **stable** (never changes)
- Prefer **single-column integer** when possible

