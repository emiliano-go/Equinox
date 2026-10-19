---
tags:
  - pandas
  - python
  - data-cleaning
  - workflow
created: 2026-10-19
---

# Dealing with Missing Data

[[Missing Data]] is present in most, if not all datasets. 

## Detecting

We can use `df.info()` to check for missing data. 

```python
df.info()
```

```bash
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 5 entries, 0 to 4
Data columns (total 3 columns):
 #   Column   Non-Null Count  Dtype
---  ------   --------------  -----
 0   Name     5 non-null      object
 1   Age      4 non-null      float64
 2   Salary   3 non-null      float64
dtypes: float64(2), object(1)
```

**Non-Null count** shows total null count.

We can use `df.isna()` and `df.isnull()` to check for Null values. They are both the same. They return True if value is missing, False if it exists.

```python
import pandas as pd

df = pd.DataFrame({
    "Name": ["Ana", None, "Luis"],
    "Age": [20, 25, None]
})

print(df.isna())
print(df.isna().sum())
```

```bash
    Name    Age
0  False  False
1   True  False
2  False   True

Name    1
Age     1
dtype: int64
```

---

## Filling

When working with missing data, its not the same having 1% of the original data missing vs having 60% of it missing.

When dealing with high amounts of missing data, you have 4 main options: Drop columns, drop rows, fill with mean/median, or fill with mode.

### Drop columns
When a column has to many missing values and isn't useful, dropping it is the best option.

### Drop rows
When some rows are missing values, its best to drop them as to now skew the data.

### Fill with mean/median
Done when rows are important but have missing numerical columns. [[Descriptive Statistics#Median|Median]] is more robust to outliers.

### Fill with mode
Done when rows are important but have missing categorical columns, such as city or gender.

```python
# Drop columns with more than 50% missing values
df = df.dropna(axis=1, thresh=len(df) * 0.5)

# Fill numerical missing values with the median
df["Age"] = df["Age"].fillna(df["Age"].median())

# Fill categorical missing values with the mode
df["City"] = df["City"].fillna(df["City"].mode()[0])
```

## What if most of the dataset is missing?

Investigate why: Missing data may follow a [[Pattern]]. Keep important columns, they may still contain valuable information that can be inferred with some filling. Consider using advanced computation methods such as [[KNN]] imputation or [[Iterative Imputation|iterative imputation]] when appropriate, and, above all, **avoid blindly deleting data**, as that may introduce [[Bias]] or lose important information.

**Rule of thumb**: Check the percentage of missing values first, understand why they're missing, and then choose the strategy based on the column's importance and data type.

# Dealing with Duplicates

Detect with `df.duplicated()` and drop with `df.drop_duplicates()`.

```python
df_clean = df.drop_duplicates(subset='user_id', keep='first')
```

# Delete or Fill?

## Delete

Delete is permanent. Only delete when:
- You have lots of data and deleting 2% means nothing.
- The missing value is the tag you want to predict

## Fill

Filling means substituting the hole for an estimated value.

**Mean**: Useful for numerical values in a [[Normal Distrubution|normal distribution]] ([[Gauss Bell]]) and without outliers.

**Median**: More robust when outliers are present.

**Mode**: Used for categorical values.

**Constant Value**: Fill with "0" of "Unknown" if we want to keep the row but we don't have accurate data.


# Transformations

**Why transform data?**
- To standardize: "es" = "esp" = "ES"
- To enrich: creating derived columns, also called [[Features]].
- To categorize: traduce values to business tags ("Big expense", "Small expense".)

This is called [[Feature Engineering]].
