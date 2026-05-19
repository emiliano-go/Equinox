---
tags:
  - database
  - concept
  - system-architecture
  - databases
  - io
created: 2026-04-28
---

# Index

An **Index** is a **separate data structure** that improves query speed.

#### Internal Structure
Most databases use a [[09_Core_Abstractions/Algorithms/B-Tree|B-Tree]] index:
- sorted structure
- Allows
	- Binary search
	- Range queries
	- Logarithmic Lookup

#### What actually happens
Without index:

```sql
SELECT * FROM Students WHERE name = "Emiliano";
```

-> Full table scan (check **every** row)

With index: **DB** -> Traverses B-Tree -> Finds matching entries -> Fetches rows

#### Types of Indexes
##### Single-column

```sql
CREATE INDEX idx_name ON Students(name);
```

##### Composite Index

```sql
CREATE INDEX idx_name_age ON Students(name, age) 
```

Order matters:
- Works for `(name)`
- Works for `(name, age)`
- **NOT** for `(age)` alone

##### Unique Index
Enforces Uniqueness (like a Primary Key)

##### Clustered vs Non-clustered
_Clustered_: Data stored in index order
*Non-clustered*: Separate structure pointing to rows

### Trade-offs
##### Pros
- Faster reads
- Faster joins
- Efficient filtering

##### Cons
- Slower inserts/updates/deletes
- More storage
- Maintenance overhead