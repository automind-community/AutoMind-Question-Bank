# Indexing, Selection & Slicing Question Bank Compiled by AutoMind Team

## Beginner: Column Selection & Basic Slicing

Use this setup for Questions 1–10:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import pandas as pd                                        %
% import numpy as np                                         %
%                                                            %
% df = pd.DataFrame({                                        %
%     'name': ['Alice', 'Bob', 'Charlie', 'Diana', 'Evan'],  %
%     'dept': ['Eng', 'HR', 'Eng', 'Sales', 'HR'],           %
%     'age': [28, 34, 29, 41, 25],                           %
%     'salary': [85000, 62000, 92000, 78000, 58000]          %
% }, index=['E1', 'E2', 'E3', 'E4', 'E5'])                   %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Select the `'name'` column as a `Series` using bracket notation `df['name']`.
2. Select the `'name'` and `'salary'` columns as a `DataFrame` using double brackets `df[['name', 'salary']]`.
3. Select the `'name'` column as a 1-column `DataFrame` (not a `Series`) using `df[['name']]`.
4. Safely access a column `'bonus'` that may not exist using `df.get('bonus', default=0)`.
5. Slice the first 3 rows of `df` using standard slice notation `df[:3]`.
6. Reverse the row order of `df` using step slicing `df[::-1]`.
7. Explain why `df['dept']` is preferred over dot notation `df.dept` (especially when column names contain spaces or match DataFrame methods like `count` or `shape`).
8. Select every second row of `df` starting from the first row using `df[::2]`.
9. Check if `'salary'` is in `df.columns` and if `'E3'` is in `df.index`.
10. Extract the scalar value of `'age'` for row `'E2'` using `df.at['E2', 'age']`.


## Intermediate: Label-Based (.loc) & Position-Based (.iloc) Indexing

Use:
```python
sales = pd.DataFrame({
    'Q1': [120, 150, 90, 200, 175],
    'Q2': [130, 160, 110, 210, 180],
    'Q3': [140, 145, 105, 220, 190],
    'Q4': [160, 170, 130, 250, 210]
}, index=['North', 'South', 'East', 'West', 'Central'])
```

11. Select the entire `'East'` row as a `Series` using `sales.loc['East']`.
12. Select rows `'North'` through `'East'` (inclusive) and columns `'Q1'` through `'Q3'` using `.loc[]`.
13. Select specific non-adjacent rows `['North', 'West']` and columns `['Q2', 'Q4']` using `.loc[]`.
14. Select the first 3 rows and first 2 columns using `.iloc[0:3, 0:2]` and explain how `.iloc` slicing differs from `.loc` slicing regarding endpoints.
15. Select the last row and the last two columns using negative integer positions in `.iloc[]`.
16. Select the single scalar at row position 2, column position 3 using fast scalar lookup `.iat[2, 3]`.
17. Update `'Q4'` for `'South'` to `185` using `.loc['South', 'Q4']`.
18. Update all values in column `'Q1'` for rows `'East'` and `'West'` by adding `10` using `.loc[]`.
19. Select all columns whose names are in `['Q1', 'Q4']` for rows where `'Q1' > 130` using `.loc` with a boolean mask.
20. Use a callable `lambda d: d['Q4'] > d['Q1'] + 30` inside `sales.loc[...]` to filter rows dynamically.


## Index Manipulation & Alignment

Use:
```python
emp = pd.DataFrame({
    'emp_id': [103, 101, 105, 102, 104],
    'name': ['Cara', 'Ava', 'Eli', 'Ben', 'Dan'],
    'score': [88, 95, 72, 91, 84]
})
```

21. Set `'emp_id'` as the index of `emp` using `set_index('emp_id')`.
22. Set `'emp_id'` as the index while keeping `'emp_id'` as a regular column (`drop=False`).
23. Reset the index back to a default integer `RangeIndex` using `reset_index()`.
24. Reset the index and discard the old index instead of inserting it as a column (`drop=True`).
25. Sort `emp` by its index in ascending order using `sort_index()`.
26. Reindex a `DataFrame` to a new index `[101, 102, 103, 106]` using `reindex()`, observing `NaN` for `106`.
27. Reindex with `fill_value=0` so missing index labels are populated with `0` instead of `NaN`.
28. Rename columns `'name'` to `'employee_name'` and `'score'` to `'rating'` using `rename(columns=...)`.
29. Rename all column names to uppercase using `emp.rename(columns=str.upper)`.
30. Give the index a name `'employee_id'` using `rename_axis('employee_id')`.


## MultiIndex (Hierarchical Indexing)

Use this MultiIndex DataFrame for Questions 31–45:

```python
arrays = [
    ['US', 'US', 'EU', 'EU', 'APAC', 'APAC'],
    ['2025', '2026', '2025', '2026', '2025', '2026']
]
idx = pd.MultiIndex.from_arrays(arrays, names=['region', 'year'])
rev = pd.DataFrame({'revenue': [400, 450, 300, 340, 250, 290], 'profit': [80, 95, 60, 72, 50, 65]}, index=idx)
```

31. Select all rows for `'US'` using `rev.loc['US']`.
32. Select the exact row for `('EU', '2026')` using `rev.loc[('EU', '2026')]`.
33. Select `'revenue'` for `('APAC', '2025')` using `rev.loc[('APAC', '2025'), 'revenue']`.
34. Select all regions for the year `'2026'` across the second index level using `rev.xs('2026', level='year')`.
35. Use `pd.IndexSlice` (`idx_slice = pd.IndexSlice`) to select all regions and only year `'2025'` for the `'profit'` column.
36. Swap the two index levels (`'region'` and `'year'`) using `swaplevel()`.
37. Sort the `MultiIndex` lexicographically after swapping levels using `sort_index()`.
38. Drop the `'year'` level from the `MultiIndex` using `droplevel('year')`.
39. Convert the `'year'` index level back into a regular column using `reset_index(level='year')`.
40. Create a `MultiIndex` for columns with levels `['Metric', 'Quarter']` using `pd.MultiIndex.from_product([['Sales', 'Cost'], ['Q1', 'Q2']])`.
41. Flatten a `MultiIndex` column header into single strings like `'Sales_Q1'` using `['_'.join(col) for col in df.columns]`.
42. Check whether a `MultiIndex` is sorted using `rev.index.is_monotonic_increasing`.
43. Reorder a 3-level `MultiIndex` using `reorder_levels([2, 0, 1])`.
44. Select multiple outer-level keys `['US', 'APAC']` from `rev` using `.loc[['US', 'APAC']]`.
45. Access the unique values of level `'region'` using `rev.index.get_level_values('region').unique()`.


## Challenge Questions: Alignment, Pitfalls & Advanced Indexing

46. **Arithmetic Index Alignment**: Given two `Series` `s1` (index `['a', 'b', 'c']`) and `s2` (index `['b', 'c', 'd']`), add them using `s1.add(s2, fill_value=0)` and explain why `s1 + s2` produces `NaN` at `'a'` and `'d'`.
47. **Chained Indexing Trap**: Explain why `df[df['age'] > 30]['salary'] = 100000` can fail or raise `SettingWithCopyWarning` / `ChainedAssignmentError`, and rewrite it cleanly using `.loc[]`.
48. **Positional Lookup for Label-Indexed Data**: Given a list of target labels `targets = ['E2', 'E5', 'E9']` (where `'E9'` is missing), safely select only the existing labels without raising `KeyError` using `df.index.intersection(targets)`.
49. **2D Coordinate Lookup**: Given a `DataFrame` `grid` and two `Series` `row_labels` and `col_labels` of equal length, extract the corresponding `(row, col)` values vectorized without a loop (using `Index.get_indexer` and NumPy fancy indexing).
50. **MultiIndex Cross-Section with `drop_level=False`**: Extract `'2026'` from `rev` using `xs(..., drop_level=False)` and explain when preserving the sliced level is useful for downstream `concat` or `merge`.


## Extended Practice: Index Objects, Set Operations & Advanced Slicing

51. Compute the union, intersection, and difference between two `pd.Index` objects `idx1` and `idx2` using `.union()`, `.intersection()`, and `.difference()`.
52. Check whether two `DataFrame` indices are identical (including order) using `df1.index.equals(df2.index)`.
53. Find the integer positions of labels `['E2', 'E4', 'E9']` in `df.index` using `df.index.get_indexer(['E2', 'E4', 'E9'])` (observing `-1` for missing labels).
54. Use `df.reindex(columns=['salary', 'name', 'bonus'], fill_value=0)` to reorder columns and add missing columns in one step.
55. Use `df.take([0, 3, 4])` to select rows by integer position and compare its performance with `.iloc[]`.
56. Select a single cell using `.loc` vs `.at` and benchmark why `.at` is faster for scalar access.
57. Slice a sorted `DatetimeIndex` using `.loc['2026-01':'2026-03']` and explain why partial string slicing requires a sorted index.
58. Use `df.select_dtypes(include='number').iloc[:, :2]` to select the first two numeric columns dynamically.
59. Create an `IntervalIndex` using `pd.IntervalIndex.from_breaks([0, 10, 20, 30])` and look up which interval contains `15` using `.get_loc(15)`.
60. Create a `CategoricalIndex` and observe how `.loc[]` and `.sort_index()` behave on categorical labels.
61. Rename a specific level of a `MultiIndex` using `rev.index.set_names('fiscal_year', level=1)`.
62. Replace all values of a `MultiIndex` level using `rev.index.set_levels(['25', '26'], level='year')`.
63. Slice a `MultiIndex` on both row and column MultiIndices simultaneously using two `pd.IndexSlice` objects.
64. Select every `n`-th row starting from row `1` using `.iloc[1::3]`.
65. Assign a new column `'tier'` conditionally using `df.loc[df['salary'] > 80000, 'tier'] = 'Senior'` and `df.loc[df['salary'] <= 80000, 'tier'] = 'Mid'`.
66. Use `df.add_prefix('emp_')` and `df.add_suffix('_2026')` to bulk-rename all columns.
67. Slice rows from `'E2'` to the end of `df` using `df.loc['E2':]`.
68. Select columns between `'dept'` and `'salary'` (inclusive) using `df.loc[:, 'dept':'salary']`.
69. Drop specific index labels `['E1', 'E5']` using `df.drop(index=['E1', 'E5'])` without `KeyError` via `errors='ignore'`.
70. Check if an index contains duplicate labels using `df.index.has_duplicates` and inspect duplicated labels with `df.index[df.index.duplicated()]`.


## Additional Challenge Questions

71. **As-Of Reindexing (`method='ffill'`)**: Reindex a daily `DataFrame` with missing dates to a complete daily `DatetimeIndex` using `reindex(full_idx, method='ffill', limit=2)`.
72. **Dynamic Column Selection by Regex + Slicing**: Select all columns matching `r'^Q[1-3]$'` and rows where their row sum exceeds `400` in a single `.loc[]` expression.
73. **MultiIndex Level Filtering**: Filter a 3-level `MultiIndex` `DataFrame` to keep only rows where level `'year'` is `'2026'` AND `'revenue' > 300`.
74. **Block Assignment via `.iloc`**: Swap the values of the first two columns of a `DataFrame` using `.iloc[:, [0, 1]] = df.iloc[:, [1, 0]].to_numpy()`.
75. **Safe `Index.get_indexer` Mapping**: Given a lookup `Series` and a `DataFrame` column of keys (some missing), map values using `lookup.reindex(keys).to_numpy()` faster than `.merge()`.

---

Try solving as many questions as possible using `.loc`, `.iloc`, `.at`, `.iat`, `.xs()`, and `pd.IndexSlice` without falling back to Python loops or chained indexing.
