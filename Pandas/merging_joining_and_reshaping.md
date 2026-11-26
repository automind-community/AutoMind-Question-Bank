# Merging, Joining & Reshaping Question Bank Compiled by AutoMind Team

## Beginner: Concatenation (pd.concat)

Use this setup for Questions 1–10:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import pandas as pd                                        %
% import numpy as np                                         %
%                                                            %
% df1 = pd.DataFrame({'id': [1, 2], 'name': ['Alice', 'Bob']})%
% df2 = pd.DataFrame({'id': [3, 4], 'name': ['Cara', 'Dan']}) %
% df_extra = pd.DataFrame({'dept': ['Eng', 'HR']})           %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Concatenate `df1` and `df2` vertically (row-wise) using `pd.concat([df1, df2])`.
2. Concatenate `df1` and `df2` vertically while resetting the resulting index to `0, 1, 2, 3` using `ignore_index=True`.
3. Concatenate `df1` and `df2` with hierarchical keys `keys=['batch1', 'batch2']` to track row origins.
4. Concatenate `df1` and `df_extra` horizontally (column-wise) using `axis=1`.
5. Concatenate two DataFrames with partially overlapping columns using `join='inner'` vs `join='outer'`.
6. Concatenate two DataFrames while raising an error if duplicate index labels exist using `verify_integrity=True`.
7. Append a single new row dictionary/DataFrame to `df1` using `pd.concat()` (since `DataFrame.append()` was removed in Pandas 2.0).
8. Concatenate a dictionary of DataFrames `{'jan': df1, 'feb': df2}` using `pd.concat()` and observe the automatic `MultiIndex`.
9. Concatenate two `Series` `s1` and `s2` along `axis=1` to form a 2-column `DataFrame` with custom column names.
10. Combine two DataFrames with identical schemas and drop any duplicate rows created during concatenation.


## Intermediate: Merging & Joining (pd.merge & df.join)

Use:
```python
users = pd.DataFrame({
    'user_id': [1, 2, 3, 4],
    'name': ['Alice', 'Bob', 'Charlie', 'Diana']
})
orders = pd.DataFrame({
    'order_id': [101, 102, 103, 104],
    'customer_id': [1, 2, 1, 5],
    'total': [50.0, 120.0, 75.0, 200.0]
})
```

11. Perform an **inner join** between `users` and `orders` matching `user_id` to `customer_id` using `pd.merge()`.
12. Perform a **left join** keeping all users even if they have no orders.
13. Perform a **right join** keeping all orders even if the `customer_id` does not exist in `users`.
14. Perform a **full outer join** (`how='outer'`) and add a `_merge` column using `indicator=True` to see which table each row came from.
15. Perform a **Cartesian product (cross join)** between two DataFrames using `pd.merge(df_a, df_b, how='cross')`.
16. Merge two DataFrames that share a non-key column `'name'` and customize disambiguation suffixes with `suffixes=('_left', '_right')`.
17. Merge on **multiple key columns** `['year', 'region']` using `on=['year', 'region']`.
18. Merge a DataFrame's column `'user_id'` with another DataFrame's **index** using `right_index=True`.
19. Validate merge cardinality using `validate='one_to_many'` to catch unexpected duplicate keys.
20. Perform an index-based join using `df_a.join(df_b, how='left', lsuffix='_a', rsuffix='_b')`.


## Specialized Merges: merge_asof & merge_ordered

Use:
```python
trades = pd.DataFrame({
    'time': pd.to_datetime(['2026-01-01 09:30:02', '2026-01-01 09:30:07', '2026-01-01 09:30:12']),
    'ticker': ['AAPL', 'AAPL', 'AAPL'],
    'price': [185.1, 185.4, 185.2]
})
quotes = pd.DataFrame({
    'time': pd.to_datetime(['2026-01-01 09:30:00', '2026-01-01 09:30:05', '2026-01-01 09:30:10']),
    'ticker': ['AAPL', 'AAPL', 'AAPL'],
    'bid': [185.0, 185.3, 185.1]
})
```

21. Match each trade to the most recent prior quote (`direction='backward'`) using `pd.merge_asof()`.
22. Match each trade to the nearest quote in time (`direction='nearest'`) within a `2s` tolerance (`tolerance=pd.Timedelta('2s')`).
23. Perform `pd.merge_asof()` grouped by `'ticker'` using `by='ticker'`.
24. Use `pd.merge_ordered()` on time-series DataFrames with `fill_method='ffill'` to align and forward-fill missing dates.
25. Filter `pd.merge(..., indicator=True)` to perform an **anti-join** (find all rows in `users` that have NO matching rows in `orders`).


## Reshaping: Pivot, Melt, Stack, Unstack & Crosstab

Use this DataFrame for Questions 26–45:

```python
sales_long = pd.DataFrame({
    'date': ['2026-01', '2026-01', '2026-02', '2026-02', '2026-01', '2026-02'],
    'region': ['East', 'West', 'East', 'West', 'East', 'West'],
    'product': ['A', 'A', 'A', 'A', 'B', 'B'],
    'revenue': [100, 150, 120, 180, 90, 110]
})
```

26. Reshape `sales_long` (for a single product) from long to wide format using `.pivot(index='date', columns='region', values='revenue')`.
27. Create a pivot table summarizing total `'revenue'` by `'date'` (rows) and `'region'` (columns) using `pd.pivot_table(..., aggfunc='sum', fill_value=0)`.
28. Add row and column totals (`'All'`) to a pivot table using `margins=True` and `margins_name='Total'`.
29. Create a pivot table with multiple aggregation functions `aggfunc=['sum', 'mean']` and multiple index levels `['region', 'product']`.
30. Unpivot (melt) a wide DataFrame `wide_df` (`id_vars=['id', 'name']`, `value_vars=['Q1', 'Q2', 'Q3']`) into long format using `pd.melt()`.
31. Customize the melted column names using `var_name='quarter'` and `value_name='sales'`.
32. Reshape wide columns named `'score_2025'`, `'score_2026'`, `'rank_2025'`, `'rank_2026'` into long format using `pd.wide_to_long()`.
33. Pivot the inner column level of a `MultiIndex` DataFrame into row index levels using `.stack()`.
34. Unstack a row index level into columns using `.unstack(fill_value=0)`.
35. Compute a contingency table (frequency matrix) of `'region'` vs `'product'` using `pd.crosstab()`.
36. Compute a normalized contingency table (row-wise percentages) using `pd.crosstab(..., normalize='index')`.
37. Transpose a `DataFrame` (swap rows and columns) using `.T`.
38. Convert a categorical column into binary indicator (dummy) columns using `pd.get_dummies(df, columns=['region'], drop_first=True, dtype=int)`.
39. Expand a column containing lists of items into one row per item using `.explode()`.
40. Reverse an `.explode()` operation by grouping and aggregating items back into lists using `groupby('id')['item'].agg(list)`.


## Advanced Reshaping & Relational Patterns

41. Perform a **self-join** on an `employees` DataFrame (`emp_id`, `name`, `manager_id`) to display each employee alongside their manager's name.
42. Use `df.update(other_df)` to overwrite non-NA values in `df` in-place based on matching index and column labels.
43. Align two DataFrames of different shapes using `df1.align(df2, join='outer', fill_value=0)`.
44. Flatten hierarchical columns produced by `pivot_table` into clean single-level column names.
45. Check for many-to-many blowups before merging by comparing `len(df1) * len(df2)` or inspecting key uniqueness with `.is_unique`.


## Challenge Questions: Complex Relational & Tidy Data Pipelines

46. **Range / Inequality Join**: Given `events` with `timestamp` and `campaigns` with `start_time` and `end_time`, match each event to the active campaign without an explicit SQL `BETWEEN` (using cross join + filter or `merge_asof`).
47. **Multi-Metric Melt & Re-Pivot**: Given a messy wide table with columns `['city', 'temp_2025', 'temp_2026', 'rain_2025', 'rain_2026']`, tidy it into `['city', 'year', 'temp', 'rain']`.
48. **Symmetric Pairwise Matrix**: Convert a long edge list `('node_a', 'node_b', 'weight')` into a full square adjacency matrix filled with `0` for missing edges using `pivot` and `reindex`.
49. **Deduplicated Left Join**: Merge `users` with `orders` so each user is joined ONLY with their single latest order (preventing row multiplication).
50. **Compare Two DataFrames**: Given `df_old` and `df_new` with identical index and columns, generate a concise diff table showing only changed cells using `df_old.compare(df_new)`.


## Extended Practice: Advanced Merging & Reshaping

51. Use `pd.merge(..., how='left', validate='many_to_one')` and explain what exception is raised when the right table has duplicate keys.
52. Merge two DataFrames on columns with different names (`left_on='emp_id', right_on='id'`) and drop the redundant `'id'` column cleanly.
53. Concatenate 3 DataFrames horizontally (`axis=1`) that have misaligned indices using `join='inner'` so only common index labels remain.
54. Use `pd.concat([s1, s2, s3], axis=1, keys=['col1', 'col2', 'col3'])` to combine multiple `Series` into a named `DataFrame`.
55. Use `df.pivot_table(..., aggfunc={'revenue': 'sum', 'units': 'mean'})` to apply different aggregations to different value columns.
56. Use `pd.crosstab(index=[df['region'], df['year']], columns=df['product'], margins=True)` for multi-level contingency tables.
57. Unstack a `MultiIndex` `Series` at a specific level by name (`s.unstack(level='region')`) rather than position.
58. Stack a `DataFrame` with `future_stack=True` (Pandas 2.1+) and explain how it handles `NaN` rows differently from legacy `stack()`.
59. Use `df.melt(id_vars='id', value_vars=df.filter(like='2026_').columns)` to dynamically select columns to unpivot.
60. Use `pd.get_dummies(s, prefix='cat', prefix_sep=':')` to customize dummy column naming.
61. Reverse one-hot encoded dummy columns back into a single categorical label column using `pd.from_dummies(dummies_df)`.
62. Combine two DataFrames by taking non-null values from `df1` first and falling back to `df2` using `df1.combine_first(df2)`.
63. Merge two DataFrames using `df1.merge(df2, on='key')` inside a method chain without breaking fluency.
64. Perform `pd.merge_asof()` with `allow_exact_matches=False` so a trade only matches strictly *earlier* quotes.
65. Use `df.explode(['tags', 'scores'])` (multi-column explode) when two list columns have matching lengths per row.
66. Flatten a 2-level column `MultiIndex` produced by `pivot_table` using `df.columns = [f"{a}_{b}" if b else a for a, b in df.columns]`.
67. Reshape a `Series` with a 2-level `MultiIndex` into a 2D matrix using `.unstack()` and convert it back using `.stack()`.
68. Use `df.reorder_levels()` after `.unstack()` and `.stack()` to restore a canonical index level order.
69. Perform a **semi-join** (keep rows in `users` that have at least one match in `orders`, without duplicating rows) using `users[users['user_id'].isin(orders['customer_id'])]`.
70. Use `df.compare(other, keep_shape=True, keep_equal=False)` to inspect diffs while preserving original DataFrame dimensions.


## Additional Challenge Questions

71. **Chained Multi-Table Star-Schema Join**: Join `fact_sales` with `dim_users`, `dim_products`, and `dim_stores` in a single fluent `.merge()` chain while validating `many_to_one` on every dimension.
72. **Point-in-Time Slowly Changing Dimension (SCD Type 2)**: Match each transaction `(user_id, tx_date)` to the user's active subscription tier at `tx_date` using `pd.merge_asof(..., by='user_id', direction='backward')`.
73. **Co-Occurrence Matrix**: Given `(order_id, product_id)` rows, build a product-by-product co-occurrence matrix showing how many orders contained both products using a self-merge and `pd.crosstab()`.
74. **Tidy Multi-Header Excel Table**: Given a `DataFrame` with 2-level column headers `('2026', 'Sales')`, `('2026', 'Profit')`, melt it into a tidy 4-column table `['region', 'year', 'metric', 'value']`.
75. **Set-Difference Between Two Tables**: Find rows present in `df_a` but missing in `df_b` across all columns using `pd.merge(df_a, df_b, how='left', indicator=True)` filtered to `'_merge == "left_only"'`.

---

Try solving as many questions as possible using `pd.concat()`, `pd.merge()`, `pd.merge_asof()`, `pd.pivot_table()`, `pd.melt()`, `.stack()`, `.unstack()`, and `pd.crosstab()` without Python `for` loops.
