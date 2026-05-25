---
tags:
  - database
  - concept
  - system-architecture
  - databases
  - io
created: 2026-04-28
---

# Foreign key

A **foreign key** is an attribute in one table that **references the [[Primary Key]]** of another table.

#### Internal Behavior
When you insert/update:
- DB checks:
		`FK value ∈ referenced PK values`
- If not -> **constrain violation**

#### Referential Integrity
Foreign keys enforce:
- No "dangling references"
- Consistency across tables

#### Actions on change
You can define what happens when the referenced row change:
```sql
FOREIGN KEY (company_id)
REFERENCES Company(id)
ON DELETE CASCADE
ON UPDATE CASCADE
```
##### Common options:
**CASCADE**
- Delete/update propagates
**SET NULL**
- FK becomes null
**RESTRICT / NO ACTION**
- Prevent operation

## Important detail: Performance
FK columns are **not always indexed automatically**, but they _should be_, because:
 - Joins depend on them
 - Deletes/updates check them
