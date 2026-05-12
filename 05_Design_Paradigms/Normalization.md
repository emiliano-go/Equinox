---
tags:
  - design-paradigm
  - database
  - concept
created: 2026-04-28
---

**Normalization** is the process of **structuring data to reduce redundancy and improve consistency**.

It's goal is to avoid duplicated data, prevent anomalies (update, insert, delete problems) and make data logically organized.

### Normalization in Relational Databases
In relational databases, normalization means organizing tables and their relationships according to formal rules called normal forms.


## Core

### First Normal Form: 1NF
- All attributes are **atomic** (no lists or nested values)
- No repeating groups

❌ Bad:

```
Student(name, phones = [123, 456])
```

✅ Good:

```
Student(name, phone)
```

### Second Normal Form: 2NF
- Must be in 1NF
- No **partial dependency** on part of a composite key

**Meaning**: Every non-key attribute depends on the **whole** primary key

### Third Normal Form: 3NF
- Must be in 2NF
- No **transitive dependencies**

**Meaning**: Non-key attributes depends **only on the primary key**, not on other non-key attributes

❌ Bad:

```
Student(id, dept_id, dept_name)
```

→ `dept_name` depends on `dept_id`, not directly on `id`

✅ Good:

```
Student(id, dept_id)
Department(dept_id, dept_name)
```

### Boyce-Codd Normal Form: BCNF
BCNF is a **stronger version of Third Normal Form** focused on eliminating certain dependency anomalies that 3NF may still allow.

A relation is in BCNF if:
**For every functional dependency $X \to Y, X$ must be a candidate key.**

#### Key concepts

##### Functional Dependency

A functional dependency: $X \to Y$ means:
*The value of X uniquely determines the value of Y.*

**Example**: `student_id → student_name`

A student ID determines exactly one student name.

##### Determinant

The **determinant** is the left side of the dependency.

In: $X \to Y$

- $X$ = Determinant

##### Candidate Key

A **candidate key** is a minimal set of attributes that uniquely identifies tuples.

### The BCNF rule

**BCNF** requires that:

$$\text{Every determinant is a candidate key}$$

**Meaning**:

- No non-key attribute may determine other attributes
- Only keys are allowed to determine values

#### Why 3NF is not always enough

3NF allows some dependencies where:

- the determinant is **not** a candidate key
- but the dependent attribute is part of a candidate key

BCNF removes these exceptions.

### Example (classic BCNF violation)

Consider:

```
Courses(student, course, professor)
```

Assume:

- A professor teaches only one course
- A student can take many courses

Functional dependencies:

$$(student, course) \to professor$$
$$professor\to course$$

---

### Candidate key

The key is:$$(student,course)$$
because together they uniquely identify tuples.

## Problem

Dependency:$$professor \to course$$
means:

- knowing the professor determines the course

But:

- `professor` is **not** a candidate key

→ BCNF violation

---

### Why this is bad

Redundancy appears:

```
(Alice, Databases, Smith)(Bob, Databases, Smith)(Carol, Databases, Smith)
```

If Smith changes course:

- many rows must be updated

This causes:

- update anomalies
- redundancy

---

### BCNF decomposition

Split into:

```
ProfessorCourse(professor, course)
StudentProfessor(student, professor)
```

Now:

- determinants are keys
- redundancy reduced

---

# Relationship with 3NF

#### 3NF

Allows some non-key determinants under special conditions.

#### BCNF

Stricter:

- every determinant must be a candidate key
- no exceptions

---

### Important trade-off

BCNF sometimes:

- requires more decomposition
- may sacrifice dependency preservation

So some systems stop at 3NF for practicality.