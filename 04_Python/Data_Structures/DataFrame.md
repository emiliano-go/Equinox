---
tags:
  - pandas
  - data-structure
created: 2026-04-20
---

# DataFrame

A two-dimensional table data structure in pandas.

> See also: [[04_Python/Libraries/pandas|pandas]]

# DataFrame Methods

Comprehensive reference for DataFrame methods and attributes.

# Attributes

## T
The transpose of the DataFrame.
```python
df.T              # transposed DataFrame
```

## at
Access a single value for a row/column label pair.
```python
df.at['row', 'col']   # get/set single value
df.at['row', 'col'] = 5
```

## attrs
Dictionary of global attributes.
```python
df.attrs         # global attributes dict
```

## axes
Return a list representing the axes.
```python
df.axes          # [row_index, column_index]
```

## columns
The column labels.
```python
df.columns      # Index of columns
```

## dtypes
Return the dtypes in the DataFrame.
```python
df.dtypes      # Series of dtypes
```

## empty
Indicator whether DataFrame is empty.
```python
df.empty       # True/False
```

## flags
Get properties associated with this pandas object.
```python
df.flags       # flags object
```

## iat
Access single value by integer position.
```python
df.iat[0, 0]      # row 0, col 0
```

## iloc
Purely integer-location based indexing.
```python
df.iloc[0, 1]     # row 0, col 1
df.iloc[0:5, :]    # first 5 rows
```

## index
The index (row labels).
```python
df.index       # Index of rows
```

## loc
Access by labels or boolean array.
```python
df.loc['row_name', 'col_name']  # single
df.loc[:, 'col_name']           # column
df.loc[df['col'] > 0]          # boolean
```

## ndim
Number of axes/dimensions.
```python
df.ndim        # 2 for DataFrame
```

## shape
Tuple representing dimensionality.
```python
df.shape      # (rows, cols)
```

## size
Number of elements.
```python
df.size       # rows * cols
```

## style
Returns Styler object.
```python
df.style      # Styler for formatting
```

## values
Numpy representation.
```python
df.values     # numpy array
```

# Methods

## abs()
Return absolute numeric values.
```python
df.abs()      # absolute values
```

## add(other, axis, level, fill_value)
Addition of DataFrame and other.
```python
df.add(other_df)
df.add(5)
```

## add_prefix(prefix, axis)
Prefix labels with string.
```python
df.add_prefix('col_')    # prefix columns
df.add_prefix('row_', axis=0)
```

## add_suffix(suffix, axis)
Suffix labels with string.
```python
df.add_suffix('_col')
```

## agg(func, axis)
Aggregate using operations over axis.
```python
df.agg('sum')
df.agg({'col1': 'sum', 'col2': 'mean'})
```

## aggregate(func, axis)
Alias for agg.
```python
df.aggregate('sum')
```

## align(other, join, axis, level, copy, ...)
Align two objects on their axes.
```python
df1.align(df2, join='outer')
```

## all(axis, bool_only, skipna)
Return whether all elements are True.
```python
df.all()
df.all(axis=1)
```

## any(axis, bool_only, skipna)
Return whether any element is True.
```python
df.any()
```

## apply(func, axis, raw, result_type, args, ...)
Apply function along axis.
```python
df.apply(np.sum)
df.apply(lambda x: x * 2)
df.apply('mean')
```

## applymap(func, na_action)
Apply function to each element.
```python
df.applymap(lambda x: str(x))
```

## asfreq(freq, method, how, normalize, ...)
Convert time series to specified frequency.
```python
df.asfreq('D')      # daily
```

## asof(where, subset)
Return last row without NaNs before where.
```python
df.asof(where_date)
```

## assign(**kwargs)
Assign new columns.
```python
df.assign(new_col=df['a'] + df['b'])
```

## astype(dtype, copy, errors)
Cast to specified dtype.
```python
df.astype({'col1': float})
df.astype('int32')
```

## at_time(time, asof, axis)
Select values at particular time of day.
```python
df.at_time('9:30')
```

## backfill()
Fill NA with next valid observation.
```python
df.backfill()
```

## between_time(start_time, end_time, ...)
Select values between times.
```python
df.between_time('9:00', '9:30')
```

## bfill()
Backfill NA values.
```python
df.bfill()
```

## bool()
Return bool of single element.
```python
df.bool()
```

## boxplot(column, by, ax, fontsize, rot, ...)
Make a box plot.
```python
df.boxplot()
```

## clip(lower, upper, axis, inplace)
Trim values at threshold.
```python
df.clip(0, 100)
df.clip(lower=0)
```

## combine(other, func, fill_value, overwrite)
Column-wise combine.
```python
df.combine(other_df, lambda x, y: x if x > y else y)
```

## combine_first(other)
Update nulls with other values.
```python
df.combine_first(other_df)
```

## compare(other, align_axis, keep_shape, ...)
Compare DataFrames and show differences.
```python
df.compare(other_df)
```

## convert_dtypes(infer_objects, convert_string, ...)
Convert to best dtypes.
```python
df.convert_dtypes()
```

## copy(deep)
Make a copy.
```python
df.copy()
df.copy(deep=True)
```

## corr(method, min_periods, numeric_only)
Compute pairwise correlation.
```python
df.corr()
df.corr('pearson')
```

## corrwith(other, axis, drop, method, ...)
Compute pairwise correlation.
```python
df.corrwith(other_df)
```

## count(axis, numeric_only)
Count non-NA cells.
```python
df.count()
df.count(axis=1)
```

## cov(min_periods, ddof, numeric_only)
Compute pairwise covariance.
```python
df.cov()
```

## cummax(axis, skipna)
Cumulative maximum.
```python
df.cummax()
df.cummax(axis=1)
```

## cummin(axis, skipna)
Cumulative minimum.
```python
df.cummin()
```

## cumprod(axis, skipna)
Cumulative product.
```python
df.cumprod()
```

## cumsum(axis, skipna)
Cumulative sum.
```python
df.cumsum()
```

## describe(percentiles, include, exclude)
Generate descriptive statistics.
```python
df.describe()
df.describe(include='object')
```

## diff(periods, axis)
First discrete difference.
```python
df.diff()
df.diff(periods=2)
```

## div(other, axis, level, fill_value)
Floating division.
```python
df.div(2)
df.div(other_df)
```

## divide(other, axis, level, fill_value)
Alias for div.
```python
df.divide(2)
```

## dot(other)
Matrix multiplication.
```python
df.dot(other_df)
```

## drop(labels, axis, index, columns, level, ...)
Drop specified labels.
```python
df.drop('col', axis=1)
df.drop(['row1', 'row2'])
```

## drop_duplicates(subset, keep, inplace, ...)
Remove duplicate rows.
```python
df.drop_duplicates()
df.drop_duplicates(subset=['col'])
```

## droplevel(level, axis)
Remove index level.
```python
df.droplevel(0)
```

## dropna(axis, how, thresh, subset, ...)
Remove missing values.
```python
df.dropna()
df.dropna(thresh=2)        # keep rows with 2+ non-NA
```

## duplicated(subset, keep)
Mark duplicate rows.
```python
df.duplicated()
```

## eq(other, axis, level)
Element-wise equal.
```python
df.eq(other_df)
df.eq(5)
```

## equals(other)
Test if objects contain same elements.
```python
df.equals(other_df)
```

## eval(expr, inplace)
Evaluate string operations on columns.
```python
df.eval('a + b')
df.eval('a > b', inplace=True)
```

## ewm(com, span, halflife, alpha, ...)
Exponentially weighted calculations.
```python
df.ewm(span=12)
```

## expanding(min_periods, axis, method)
Provide expanding window calculations.
```python
df.expanding().sum()
```

## explode(column, ignore_index)
Transform list elements to rows.
```python
df.explode('col')
```

## ffill()
Forward fill NA values.
```python
df.ffill()
```

## fillna(value, method, axis, inplace, ...)
Fill NA values.
```python
df.fillna(0)
df.fillna(method='ffill')
```

## filter(items, like, regex, axis)
Subset rows/columns.
```python
df.filter(like='test')
df.filter(regex='^a')
```

## first(offset)
Select initial periods.
```python
df.first('5D')
```

## first_valid_index()
Return index of first non-NA.
```python
df.first_valid_index()
```

## floordiv(other, axis, level, fill_value)
Integer division.
```python
df.floordiv(2)
```

## from_dict(data, orient, dtype, columns)
Construct from dict.
```python
pd.from_dict({'a': [1, 2], 'b': [3, 4]})
```

## from_records(data, index, exclude, ...)
Convert structured array to DataFrame.
```python
pd.from_records(array)
```

## ge(other, axis, level)
Greater than or equal.
```python
df.ge(5)
```

## get(key, default)
Get column or default.
```python
df.get('col')
df.get('missing', default=0)
```

## groupby(by, axis, level, as_index, sort, ...)
Group DataFrame.
```python
df.groupby('col').sum()
df.groupby(['col1', 'col2']).mean()
```

## gt(other, axis, level)
Greater than.
```python
df.gt(5)
```

## head(n)
Return first n rows.
```python
df.head(10)
```

## hist(column, by, grid, xlabelsize, xrot, ...)
Make histogram.
```python
df.hist()
```

## idxmax(axis, skipna, numeric_only)
Index of first maximum.
```python
df.idxmax()
```

## idxmin(axis, skipna, numeric_only)
Index of first minimum.
```python
df.idxmin()
```

## infer_objects(copy)
Infer better dtypes for object columns.
```python
df.infer_objects()
```

## info(verbose, buf, max_cols, memory_usage, ...)
Print concise summary.
```python
df.info()
```

## insert(loc, column, value, allow_duplicates)
Insert column.
```python
df.insert(0, 'new_col', values)
```

## interpolate(method, axis, limit, inplace, ...)
Fill NaN using interpolation.
```python
df.interpolate()
df.interpolate(method='linear')
```

## isetitem(loc, value)
Set value at position.
```python
df.isetitem(0, value)
```

## isin(values)
Check if elements in values.
```python
df.isin([1, 2, 3])
```

## isna()
Detect missing values.
```python
df.isna()
df.isna().sum()
```

## isnull()
Alias for isna.
```python
df.isnull()
```

## items()
Iterate over (column, Series) pairs.
```python
for col, series in df.items():
    print(col)
```

## iterrows()
Iterate over (index, Series) pairs.
```python
for idx, row in df.iterrows():
    print(idx, row)
```

## itertuples(index, name)
Iterate as namedtuples.
```python
for row in df.itertuples():
    print(row)
```

## join(other, on, how, lsuffix, rsuffix, ...)
Join columns.
```python
df.join(other_df)
df.join(other_df, how='outer')
```

## keys()
Get info axis.
```python
df.keys()      # alias for columns
```

## kurt(axis, skipna, numeric_only)
Unbiased kurtosis.
```python
df.kurt()
```

## kurtosis(...)
Alias for kurt.
```python
df.kurtosis()
```

## last(offset)
Select final periods.
```python
df.last('5D')
```

## last_valid_index()
Index of last non-NA.
```python
df.last_valid_index()
```

## le(other, axis, level)
Less than or equal.
```python
df.le(5)
```

## lt(other, axis, level)
Less than.
```python
df.lt(5)
```

## map(func, na_action)
Apply function elementwise.
```python
df.map(lambda x: x * 2)
```

## mask(cond, other, inplace, axis, level)
Replace values where cond is True.
```python
df.mask(df < 0, 0)
```

## max(axis, skipna, numeric_only)
Maximum.
```python
df.max()
```

## mean(axis, skipna, numeric_only)
Mean.
```python
df.mean()
```

## median(axis, skipna, numeric_only)
Median.
```python
df.median()
```

## melt(id_vars, value_vars, var_name, ...)
Unpivot DataFrame.
```python
df.melt(id_vars=['id'])
```

## memory_usage(index, deep)
Memory usage in bytes.
```python
df.memory_usage()
df.memory_usage(deep=True)
```

## merge(right, how, on, left_on, right_on, ...)
Merge DataFrames.
```python
df.merge(right, on='key')
df.merge(right, left_on='lkey', right_on='rkey')
```

## min(axis, skipna, numeric_only)
Minimum.
```python
df.min()
```

## mod(other, axis, level, fill_value)
Modulo.
```python
df.mod(2)
```

## mode(axis, numeric_only, dropna)
Mode (most frequent values).
```python
df.mode()
```

## mul(other, axis, level, fill_value)
Multiplication.
```python
df.mul(2)
```

## multiply(other, axis, level, fill_value)
Alias for mul.
```python
df.multiply(2)
```

## ne(other, axis, level)
Not equal.
```python
df.ne(5)
```

## nlargest(n, columns, keep)
Return first n rows ordered by columns.
```python
df.nlargest(10, 'col')
```

## notna()
Detect existing values.
```python
df.notna()
```

## notnull()
Alias for notna.
```python
df.notnull()
```

## nsmallest(n, columns, keep)
Return first n rows ascending.
```python
df.nsmallest(10, 'col')
```

## nunique(axis, dropna)
Count distinct elements.
```python
df.nunique()
```

## pad()
Alias for ffill.
```python
df.pad()
```

## pct_change(periods, fill_method, limit, freq)
Fractional change.
```python
df.pct_change()
```

## pipe(func, *args, **kwargs)
Chainable functions.
```python
df.pipe(func)
df.pipe(func, arg1, arg2)
```

## pivot(columns, index, values)
Reshape by columns.
```python
df.pivot(index='idx', columns='col', values='val')
```

## pivot_table(values, index, columns, ...)
Spreadsheet-style pivot.
```python
df.pivot_table(values='val', index='idx', columns='col', aggfunc='sum')
```

## pop(item)
Return and drop column.
```python
df.pop('col')
```

## pow(other, axis, level, fill_value)
Exponential power.
```python
df.pow(2)
```

## prod(axis, skipna, numeric_only, min_count)
Product.
```python
df.prod()
```

## product(...)
Alias for prod.
```python
df.product()
```

## quantile(q, axis, numeric_only, ...)
Values at given quantile.
```python
df.quantile(0.5)
df.quantile([0.25, 0.75])
```

## query(expr, inplace)
Query with boolean expression.
```python
df.query('a > b')
df.query('a > b', inplace=True)
```

## radd(other, axis, level, fill_value)
Reverse addition.
```python
df.radd(5)    # 5 + df
```

## rank(axis, method, numeric_only, ...)
Numerical ranks.
```python
df.rank()
df.rank(method='min')
```

## rdiv(other, axis, level, fill_value)
Reverse division.
```python
df.rdiv(1)    # 1 / df
```

## reindex(labels, index, columns, axis, ...)
Conform to new index.
```python
df.reindex(['a', 'b', 'c'])
```

## reindex_like(other, method, copy, limit, ...)
Match other index.
```python
df.reindex_like(other)
```

## rename(mapper, index, columns, axis, copy, ...)
Rename labels.
```python
df.rename(columns={'old': 'new'})
df.rename(index={0: 'a'})
```

## rename_axis(mapper, index, columns, axis, ...)
Set axis name.
```python
df.rename_axis('rows')
```

## reorder_levels(order, axis)
Reorder index levels.
```python
df.reorder_levels([1, 0])
```

## replace(to_replace, value, inplace, limit, ...)
Replace values.
```python
df.replace(0, -1)
df.replace({'a': 1, 'b': 2})
```

## resample(rule, axis, closed, label, ...)
Resample time series.
```python
df.resample('D').sum()
```

## reset_index(level, drop, inplace, ...)
Reset index.
```python
df.reset_index()
```

## rfloordiv(other, axis, level, fill_value)
Reverse floor division.
```python
df.rfloordiv(10)   # 10 // df
```

## rmod(other, axis, level, fill_value)
Reverse modulo.
```python
df.rmod(10)    # 10 % df
```

## rmul(other, axis, level, fill_value)
Reverse multiplication.
```python
df.rmul(2)    # 2 * df
```

## rolling(window, min_periods, center, ...)
Rolling window calculations.
```python
df.rolling(7).mean()
```

## round(decimals)
Round values.
```python
df.round(2)
```

## rpow(other, axis, level, fill_value)
Reverse power.
```python
df.rpow(2)    # 2 ** df
```

## rsub(other, axis, level, fill_value)
Reverse subtraction.
```python
df.rsub(1)    # 1 - df
```

## rtruediv(other, axis, level, fill_value)
Reverse true division.
```python
df.rtruediv(1)   # 1 / df
```

## sample(n, frac, replace, weights, ...)
Random sample.
```python
df.sample(5)
df.sample(frac=0.1)
```

## select_dtypes(include, exclude)
Select by dtype.
```python
df.select_dtypes(include='number')
df.select_dtypes(exclude='object')
```

## sem(axis, skipna, ddof, numeric_only)
Standard error of mean.
```python
df.sem()
```

## set_axis(labels, axis, copy)
Assign index.
```python
df.set_axis(['a', 'b', 'c'])
```

## set_flags(copy, allows_duplicate_labels)
Update flags.
```python
df.set_flags(allows_duplicate_labels=True)
```

## set_index(keys, drop, append, inplace, ...)
Set index from columns.
```python
df.set_index('col')
```

## shift(periods, freq, axis, fill_value, suffix)
Shift index.
```python
df.shift(1)       # shift forward
df.shift(-1)     # shift backward
```

## skew(axis, skipna, numeric_only)
Skewness.
```python
df.skew()
```

## sort_index(axis, level, ascending, ...)
Sort by index.
```python
df.sort_index()
```

## sort_values(by, axis, ascending, ...)
Sort by values.
```python
df.sort_values('col')
df.sort_values(['col1', 'col2'])
```

## squeeze(axis)
Squeeze to scalar.
```python
df.squeeze()
```

## stack(level, dropna, sort, future_stack)
Stack columns to index.
```python
df.stack()
```

## std(axis, skipna, ddof, numeric_only)
Sample standard deviation.
```python
df.std()
```

## sub(other, axis, level, fill_value)
Subtraction.
```python
df.sub(1)
```

## subtract(other, axis, level, fill_value)
Alias for sub.
```python
df.subtract(1)
```

## sum(axis, skipna, numeric_only, min_count)
Sum.
```python
df.sum()
```

## swapaxes(axis1, axis2, copy)
Interchange axes.
```python
df.swapaxes(0, 1)
```

## swaplevel(i, j, axis)
Swap levels.
```python
df.swaplevel(0, 1)
```

## tail(n)
Return last n rows.
```python
df.tail(10)
```

## take(indices, axis)
Select by position.
```python
df.take([0, 2, 4])
```

## to_clipboard(excel, sep)
Copy to clipboard.
```python
df.to_clipboard()
```

## to_csv(path_or_buf, sep, na_rep, ...)
Write to CSV.
```python
df.to_csv('file.csv')
df.to_csv()
```

## to_dict(orient, into, index)
Convert to dictionary.
```python
df.to_dict()
df.to_dict('records')
```

## to_excel(excel_writer, sheet_name, ...)
Write to Excel.
```python
df.to_excel('file.xlsx')
df.to_excel('file.xlsx', sheet_name='sheet1')
```

## to_feather(path, **kwargs)
Write Feather format.
```python
df.to_feather('file.feather')
```

## to_gbq(destination_table, project_id, ...)
Write to BigQuery.
```python
df.to_gbq('table', 'project')
```

## to_hdf(path_or_buf, key, mode, ...)
Write to HDF5.
```python
df.to_hdf('file.h5', key='df')
```

## to_html(buf, columns, col_space, header, ...)
Render as HTML table.
```python
df.to_html()
```

## to_json(path_or_buf, orient, date_format, ...)
Convert to JSON.
```python
df.to_json()
df.to_json(orient='records')
```

## to_latex(buf, columns, header, index, ...)
Render to LaTeX.
```python
df.to_latex()
```

## to_markdown(buf, mode, index, storage_options)
Print in Markdown.
```python
df.to_markdown()
```

## to_numpy(dtype, copy, na_value)
Convert to numpy array.
```python
df.to_numpy()
```

## to_orc(path, engine, index, engine_kwargs)
Write ORC format.
```python
df.to_orc('file.orc')
```

## to_parquet(path, engine, compression, ...)
Write Parquet format.
```python
df.to_parquet('file.parquet')
```

## to_period(freq, axis, copy)
Convert to PeriodIndex.
```python
df.to_period('D')
```

## to_pickle(path, compression, protocol, ...)
Pickle to file.
```python
df.to_pickle('file.pkl')
```

## to_records(index, column_dtypes, index_dtypes)
Convert to record array.
```python
df.to_records()
```

## to_sql(name, con, schema, if_exists, ...)
Write to SQL.
```python
df.to_sql('table', con)
```

## to_stata(path, convert_dates, ...)
Export to Stata.
```python
df.to_stata('file.dta')
```

## to_string(buf, columns, col_space, header, ...)
Console output.
```python
df.to_string()
```

## to_timestamp(freq, how, axis, copy)
Cast to timestamps.
```python
df.to_timestamp()
```

## to_xarray()
Convert to xarray.
```python
df.to_xarray()
```

## to_xml(path_or_buffer, index, root_name, ...)
Render to XML.
```python
df.to_xml()
```

## transform(func, axis)
Transform columns.
```python
df.transform(lambda x: x * 2)
```

## transpose(*args, copy)
Transpose.
```python
df.T
df.transpose()
```

## truediv(other, axis, level, fill_value)
True division.
```python
df.truediv(2)
```

## truncate(before, after, axis, copy)
Truncate before/after.
```python
df.truncate(before='2020-01-01')
```

## tz_convert(tz, axis, level, copy)
Convert timezone.
```python
df.tz_convert('UTC')
```

## tz_localize(tz, axis, level, copy, ...)
Localize timezone.
```python
df.tz_localize('UTC')
```

## unstack(level, fill_value, sort)
Pivot level to columns.
```python
df.unstack()
```

## update(other, join, overwrite, ...)
Update with other values.
```python
df.update(other_df)
```

## value_counts(subset, normalize, sort, ...)
Frequency of each row.
```python
df.value_counts()
```

## var(axis, skipna, ddof, numeric_only)
Variance.
```python
df.var()
```

## where(cond, other, inplace, axis, level)
Replace where False.
```python
df.where(df > 0, -1)
```

## xs(key, axis, level, drop_level)
Cross-section.
```python
df.xs('value', level='name')
```