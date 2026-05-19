---
tags:
  - database
  - concept
  - system-architecture
  - databases
  - io
created: 2026-04-28
---

# Junction Table

A **junction table** is a table used to represent a [[Relational Databases#Many-to-Many|Many-to-Many]] relationship between two tables.

Since relational databases don't support N:M relationships directly, you **decompose** them into two 1:N relationships using this intermediate table.

### Structure
A junction table typically contains:
- [[08_System_Architecture/Databases/Relational_Databases/Foreign key|Foreign Keys]] to both related tables
- Often a **composite primary key** made from those foreign keys

### Example
Students <-->  Course

```sql
Enrollments(
    student_id → Students.id,
    course_id → Courses.id,
    PRIMARY KEY (student_id, course_id)
)
```

### Key Properties
- Each row represent **one association**
- Prevents duplicate relationships (via composite PK)
- Can store **extra attributes** about the relationship: `grade, enrolled_at, status`
