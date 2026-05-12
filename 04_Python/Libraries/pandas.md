---
tags:
  - pandas
  - library
  - python
created: 2026-04-16
---

> Part of the [[00_Index/Data Science]] workflow.

pandas is a Python library that enables data to be handled as numeric tables.

It uses unique data structures that enable processing of various types of data.

> **In short:**
> You can handle data as if you were using Excel

|                                  Strengths                                   |       Weaknesses        |
| :--------------------------------------------------------------------------: | :---------------------: |
| Has methods for processing numerical data, time-series and character strings | Slow calculation speed  |
|          Strong in statistical processing such as data aggregation           | High Memory consumption |
|         Read and writes multiple file formats: csv, excel, json, etc         |  Steep learning curve   |
# Data Structures

Common data structures used in pandas are Series and Data Frames

## Series

Series are 1D arrays (also called vectors).

See [[04_Python/Data_Structures/Series]]

## Data Frames     | Row name  |
| :-- | --------- |
| 1   | 123412312 |
| 2   | 2352123   |
| 3   | 3456234   |
| 4   | 213123    |
| 5   | 546342    |
These can be represented by a Numpy 1D array.

In pandas, a series is defined using `pandas.Series`

```python
from pandas import Series

series = Series([1,1,4,6,7,8])
print(series)

# Output
0 1
1 1
2 4
3 6
4 7
5 8

```

A `Series` object has both indices and elements. Indices can be defined using the `index` parameter.

```python
series = Series([1, 1, 2, 3, 5, 8],
                index=["a", "b", "c", "d", "e", "f"])

print(series)

# Output

a 1
b 1 
c 2 
d 3 
e 5 
f 8
```

Indexes and Values can also be retrieved separately:

```python
indexes = series.index
values = series.values
```
## Data Frames
Data Frames are 2D matrices (also called just matrices), separated in rows and columns.

|     | Column 1 | Column 2 | Column 3 |
| --- | -------- | -------- | -------- |
| 1   | 21342134 | Tokyo    | 1990     |
| 2   | 8723423  | Osaka    | 1989     |
| 3   | 23746212 | Kyoto    | 1951     |
| 4   | 21380947 | Tokyo    | 2001     |
These can be represented by a Numpy 2D array with row and column labels. Row labels are called **index** and Column labels are called **columns**. 

In pandas, a Data Frame is defined using `pandas.DataFrame`

```python
from pandas import DataFrame

data = {
'ID':['100', '101', '102', '103', '104'],
'City':['Tokyo', 'Osaka', 'Kyoto', 'Hokkaido', 'Tokyo'],
'Birth_year':[1990, 1989, 1992, 1997, 1982],
'Name':['Hiroshi', 'Akiko', 'Yuki', 'Satoru', 'Steve']
}

df = DataFrame(data)

print(df)

# Output
  ID  City     Birth_year Name 
0 100 Tokyo    1990       Hiroshi 
1 101 Osaka    1989       Akiko 
2 102 Kyoto    1992       Yuki 
3 103 Hokkaido 1997       Satoru 
4 104 Tokyo    1982       Steve

```

You can use the `.head()` method to print the 5 first rows.

See [[04_Python/Data_Structures/DataFrame]]

## How to read Data

To read data with pandas, you use one of the following pandas functions:
- `pd.read_csv()` → CSV
- `pd.read_table()` → delimited text (TSV, etc.)
- `pd.read_fwf()` → fixed-width text
- `pd.read_excel()` → Excel (.xls, .xlsx)
- `pd.read_json()` → JSON
- `pd.read_xml()` → XML
- `pd.read_html()` → HTML tables
- `pd.read_sql()` → SQL query/table
- `pd.read_sql_query()` → SQL query
- `pd.read_sql_table()` → SQL table
- `pd.read_parquet()` → Parquet
- `pd.read_feather()` → Feather
- `pd.read_orc()` → ORC
- `pd.read_pickle()` → Pickle
- `pd.read_hdf()` → HDF5
- `pd.read_sas()` → SAS
- `pd.read_spss()` → SPSS
- `pd.read_stata()` → Stata

```python
import pandas as pd

my_data = pd.read_csv('route/to/your/csv.csv')
```

Now, to visualize said data:

```python
my_data.head()
```

Let's take an example using [Hernan4444's Anime List Database](https://github.com/Hernan4444/MyAnimeList-Database):

```python
anime_data = pd.read_csv("MyAnimeList-Database-master/data/anime.csv")

anime_data.head()

# Output

# Output is too big, do it yourself
```

> Be aware that the `head()` method can take an optional integer parameter, which sets how many rows should be displayed. Eg: `anime_data.head(10)` displays the first 10 rows.

## Basic Data Evaluation
To get some basic information about our data, we can use the `.info()` method.

```python
anime_data.info()

# Output

<class 'pandas.core.frame.DataFrame'>
RangeIndex: 17562 entries, 0 to 17561

Data columns (total 35 columns):
 #   Column         Non-Null Count  Dtype
---  ------         --------------  -----
 0   MAL_ID         17562 non-null  int64
 1   Name           17562 non-null  object
 2   Score          17562 non-null  object
 3   Genres         17562 non-null  object
 4   English name   17562 non-null  object
 5   Japanese name  17562 non-null  object
 6   Type           17562 non-null  object
 7   Episodes       17562 non-null  object
 8   Aired          17562 non-null  object
 9   Premiered      17562 non-null  object
10   Producers      17562 non-null  object
11   Licensors      17562 non-null  object
12   Studios        17562 non-null  object
13   Source         17562 non-null  object
14   Duration       17562 non-null  object
15   Rating         17562 non-null  object
16   Ranked         17562 non-null  object
17   Popularity     17562 non-null  int64
18   Members        17562 non-null  int64
19   Favorites      17562 non-null  int64
...
33   Score-2        17562 non-null  object
34   Score-1        17562 non-null  object

dtypes: int64(9), object(26)
memory usage: 4.7+ MB
```

This allows us to see the data type of each column, how many rows there are, how many missing values, etc.

You can also use the `.describe()` method to calculate basic statistics about quantitative data.

```python
anime_data.describe()

# Output

# Once again, output is too big
```
### Determination of NaN

**Nan** (**N**ot **a** **N**umber) represents null data, missing data.

We need to filter missing data as to avoid miscalculation. We use the `isnull()` method to check for null values.

```python
anime_data.isnull()

# Output
||MAL_ID|Name|Score|Genres|Type|Aired|Studios|Source|
|---|---|---|---|---|---|---|---|---|
|0|False|False|False|False|False|False|False|False|
|1|False|False|False|False|False|False|False|False|
```

To find the total number of null values, we just add the `sum()` method after.

```python
anime_data.isnull().sum()
```

### Sorting

To sort value by index:

```python
anime_data.sort_index()
```

To sort by value in a specific column:

```python
anime_data.sort_values(by="Score", ascending=False)
```

## Merging Data

See [[Merging Data]] for theory.

To merge datasets, we use `pd.merge()`.

```python
pd.merge(dataset1, dataset2)
```

Without arguments, the default behavior of `merge()` is **Inner Join**.

You can specify a key passing the `on` parameter.

```python
pd.merge(dataset1, dataset2, on="ValueToFilter")
```

This keeps all the rows that match on the column `ValueToFilter`.

We can also filter columns with different names by passing the `left_on` and `right_on` parameters.

```python
import pandas as pd

users = pd.DataFrame({
    "user_id": [1, 2, 3],
    "name": ["Alice", "Bob", "Charlie"]
})

orders = pd.DataFrame({
    "customer_id": [1, 1, 2],
    "product": ["Book", "Pen", "Laptop"]
})
```

The matching columns are `users.user_id` and `orders.customer_id`.

```python
pd.merge(
    users,
    orders,
    left_on="user_id",
    right_on="customer_id"
)

# With multiple columns

pd.merge(
    df1,
    df2,
    left_on=["id", "year"],
    right_on=["customer", "date"]
)
```

**Left outer joins** specify `how="left"`.

```python
pd.merge(df1, df2, how="left")
```

**Right outer joins** work the same but with `how="right"`.

##### Full outer join

Full outer joins works by extracting data that doesn't exist in either DataFrame.

```python
pd.merge(df1, df2, how="outer")
```

#### Index Merge

To merge by index we use the `df.join()` method.

```python
import pandas as pd

df1 = pd.DataFrame({
    "name": ["Alice", "Bob", "Charlie"]
}, index=[1, 2, 3])

df2 = pd.DataFrame({
    "age": [25, 30, 40]
}, index=[1, 2, 4])

df1.join(df2)

# Outout

      name   age
1    Alice  25.0
2      Bob  30.0
3  Charlie   NaN
```


### Concatenating Data

`pd.concat` is used to concatenate data without specifying keys.ç

#### Vertical join

The default is to simply connect vertically. The `pd.concat()` is often used to vertically stack data with identical columns. You can pass the `sort=True/False` argument to sort.

```python
import pandas as pd

df1 = pd.DataFrame({
    "name": ["Alice", "Bob"],
    "age": [25, 30]
})

df2 = pd.DataFrame({
    "name": ["Charlie"],
    "city": ["Paris"]
})

result = pd.concat([df1, df2], ignore_index=True)

# Output

      name   age   city
0    Alice  25.0    NaN
1      Bob  30.0    NaN
2  Charlie   NaN  Paris
```

#### Horizontal Join

To join horizontally, specify an axis for the `axis` argument. The `axis=0` is the row and `axis=1` is the column. So here you need to specify `axis=1`. In this case, they will be tied by `index` and the `columns` will be joined as they are. If `axis=0` is specified, the columns will be joined vertically. Keep in mind that this `axis` argument is used in other situations as well.

```python
pd.concat([df1, df2], axis=1)
```

## Transforming Data

To delete columns or rows in a `DataFrame` object, you mainly use `drop()` method.

For deleting rows: Specify the `Index` of the rows you want to delete as a list in the first argument. Set `axis` to **0**.

For deleting columns: Specify the column names you want to delete as a list in the first argument. Set `axis` to **1**.

After deletion, we should use the `reset_index()` method to reassign a new index.

```python

import pandas as pd

df = pd.DataFrame({
    "name": ["Alice", "Bob", "Charlie"],
    "age": [25, 30, 22],
    "city": ["Paris", "London", "Rome"]
})

# Output

      name  age    city
0    Alice   25   Paris
1      Bob   30  London
2  Charlie   22    Rome

# Drop columns

df.drop(columns=["city"])
# Is the same as:
df.drop("city", axis=1)

# Output

      name  age
0    Alice   25
1      Bob   30
2  Charlie   22

# Drop rows by index

df.drop(index=[1])
# Is the same as:
df.drop(1)

# Output

      name  age   city
0    Alice   25  Paris
2  Charlie   22   Rome

# Drop multiple rows

df.drop([0, 2])

# Output

  name  age    city
1  Bob   30  London
```

Other arguments are:

```python
# Prevents errors if a label doesn't exist:
df.drop(columns=["salary"], errors="ignore")

# Modify the original DataFrame instead of returning a new one:
df.drop(columns=["city"], inplace=True)
```

### Duplicate Data

The `duplicated()` method returns `True` if a duplicate exists in the same column.

```python
df["Name"].duplicated()
```

The `drop_duplicates()` method returns the resulting data **after** removing duplicates.

```python
df["Name"].drop_duplicates()
```

## Mapping

**Mapping** is a function that pulls data corresponding to a common key from one (reference) table to the other.

For example, `anime_list` has a column, `watching_status`, which contains numeric codes that represent a user's anime watching status, such as 1 for "Watching", 2 for "Completed", 3 for "On-Hold", 4 for "Dropped", and 6 for "Plan to Watch". We also know that other values, 0, 5, 33, 55, are invalid statuses, so we will drop those rows.

First, prepare a dictionary that maps each code to its category name.

```python
# Reference data

status_map = {
	1: "Watching",
	2: "Completed",
	3: "On-Hold",
	4: "Dropped",
	6: "Plan to Watch"
}
```

Then we apply it to the watching_status column.

```python
# Drop invalid rows first
invalid_status = [0, 5, 33, 55]

# Use ~ to represent NOT
anime_list = anime_list[~anime_list['watching_status'].isin(invalid_status)]
anime_list["status_label"] = anime_list["watching_status"].map(status_map)
```

You can also use a [[Lambda Functions|lambda function]] to map data.

```python
anime_data_extracted['ScoreCategory'] = anime_data_extracted['Score'].map(lambda x: 'Low' if x < 5 else ('Average' if x <= 7 else 'High'))
```

### Bin Splitting

This is a useful feature when you want to divide data into some discrete range for aggregation.

For example, as shown below, you can prepare a list to bin the scores per anime. Since the scores range from 0 to 10, let's create 5 bins (0 to 2, 2 to 4, ...). We use Pandas' `pd.cut()` function for bin splitting. In the `pd.cut()` function, the first argument is the data to be split and the second argument is the boundary value to be split.

```python
scores = [0, 2, 4, 6, 8, 10]

anime_data_cut_by_score = pd.cut(anime_data_extracted["Score"], scores)
```

The "(8, 10]" means that it **does not** include 8 but **does** include 10. In other words, the specified criterion is used as the delimiter "more than ~ and less than or equal to ~". This behavior can be changed by specifying the `left` or `right` option to the `pd.cut()` function.

## Missing Data

When handling data, there is always the presence of missing data and outlier data. In this section, you will learn how to determine and handle missing and abnormal data at a basic foundation level.

We will use the `data` dataset. The data contains `Unknown`, which should be treated as missing values. We will first convert all missing values as NaNs (`np.nan`).

```python
data = anime_data.replace('Unknown', np.nan)
```

### Listwise Deletion

To remove all rows with NaNs, use the `dropna()` method. This is called **listwise deletion**.

```python
data.dropna()
```

### Pairwise Deletion

As you can see from the results, listwise deletion can lead to a situation where the original 10 rows of data are extremely small and the data is completely unusable. In this case, there is a way to ignore the missing column data and use only the available data. This is called **pairwise deletion**. In pairwise deletion, the `dropna` method is applied after extracting the columns you want to use.

### Fill with `fillna`

Another method is to use `fillna()` method by passing a value to fill in the `NaN`.

For example, we can fill the missing values in `Score` with -1 using `fillna(-1)`.

```python
data["Score"] = data["Score"].fillna(-1)
```

Another method is to use the mean value to fill in the blanks. This is called the **mean value assignment method** and uses the `mean` method. Note that when dealing with time series data, this method may include future information (missing data in the past is filled with a mean value using future data).

```python
df = pd.DataFrame(...)
df.fillna(df.mean())
```

### Fill with the Previous Value
The `ffill()` method can be applied to fill with the value of the previous row.

```python
df = pd.DataFrame(...)
df.ffill()
```

This process can be used in financial time series data processing and is useful.