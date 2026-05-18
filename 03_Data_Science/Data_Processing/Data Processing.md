---
tags:
  - data-science
  - concept
created: 2026-04-28
---
**Data Processing** is the **Scrub** step of the OSEMN Workflow.

The point of data processing is to turn unstructured, raw data, into a usable dataset to study.

The steps to process said raw data vary depending on said data and the project itself, but common steps include:
- Assessing data quality
- Removing irrelevant or duplicate data points
- Imputing missing values (guessing what the value should be)
- Combining different data sets (SQL Joins, pandas Merge, etc)
- Loading the data into it's final location
- Documenting the transformation taken for future reference

This is (usually) the longest step of the OSEMN workflow, but it's also the most useful one. Data-centric approaches to projects usually yield better results.

**Data Processing** uses ETL (Extract, Transform, Load) tools, like Pentaho, Oracle DI, to extract and transform data. It also uses languages like **Python**, **R** and **Julia** to make detailed analysis.

### Preparation and cleaning of data
It's the process to **detect and correct** errors, inconsistencies, missing and duplicate values, in a data set, to guarantee it's quality.

Missing values are usually empty cells or without information (0, `null`, etc), while inconsistencies represent wrongly formatted data (dates, texts, etc).
