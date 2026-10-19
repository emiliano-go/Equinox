---
tags:
  - data-science
  - concept
  - data-cleaning
created: 2026-10-12
---

In Data science and programming, missing data can be represented in different ways.


# Types of Missing Data
## NaN
NaN (Not a Number) is the technical standard to represent missing values in numerical columns. 

For a computer, NaN is a float.

## Null

Used in most programming languages as "empty" or "absence of value", its also an SQL keyword indicating a value that does not exist.

## None

Default empty value in Python. Pandas auto-converts None to NaN when loading data to a Dataframe.

## Empty strings: ""

Empty strings `""` are NOT **NULL**, but are still missing data. Should NOT be converted to null, but instead marked as N/A.

# Why is there missing data?

Data can be missing from datasets due to a variety of reasons. "" can appear both because a user decided to left the blank space, or because the text capture was not working. Integration errors can cause data to be dropped, or just because data was dropped in previous steps.

**Golden Rule:** Never clean data without knowing its context. Deleting rows whose "Discount" column is Null means deleting clients that payed the full price.


