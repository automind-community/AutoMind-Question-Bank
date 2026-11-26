# Data Cleaning & Missing Data Question Bank Compiled by AutoMind Team

## Beginner: Detecting & Counting Missing Values

Use this setup for Questions 1–10:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import pandas as pd                                        %
% import numpy as np                                         %
%                                                            %
% df = pd.DataFrame({                                        %
%     'id': [1, 2, 3, 4, 5, 6],                              %
%     'name': ['Alice', 'Bob', None, 'Diana', 'Evan', np.nan],%
%     'age': [25, np.nan, 30, 28, np.nan, 35],               %
%     'score': [88.5, 92.0, np.nan, 76.0, 81.5, np.nan],     %
%     'joined': pd.to_datetime(['2024-01-01', None,          %
%                '2024-03-15', '2024-04-01', '2024-05-10',   %
%                pd.NaT])                                    %
% })                                                         %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Detect all missing values in `df` as a boolean DataFrame using `df.isna()`.
2. Count the number of missing values in each column using `df.isna().sum()`.
3. Compute the percentage of missing values in each column using `df.isna().mean() * 100`.
4. Count the total number of missing values across the entire `DataFrame`.
5. Check whether each row has **at least one** missing value using `df.isna().any(axis=1)`.
6. Filter and display only the rows where `'score'` is NOT missing using `df['score'].notna()`.
7. Check whether `'age'` has any missing values using `df['age'].hasnans`.
8. Count how many rows have **all** values present (zero missing values).
9. Explain why `np.nan == np.nan` evaluates to `False` and why `df['age'] == np.nan` should never be used.
10. Distinguish between `np.nan`, `None`, `pd.NA`, and `pd.NaT` in Pandas columns.


## Intermediate: Dropping & Filling Missing Values

Use the same `df` for Questions 11–25:

11. Drop all rows that contain **any** missing value using `df.dropna()`.
12. Drop rows only if **all** values in the row are missing (`how='all'`).
13. Drop columns that contain any missing value (`axis=1`).
14. Keep only rows that have at least 4 non-null values using `df.dropna(thresh=4)`.
15. Drop rows where `'name'` or `'score'` is missing using `subset=['name', 'score']`.
16. Fill all missing values in `'name'` with `'Unknown'` using `fillna()`.
17. Fill missing values in `'age'` with the median age of `'age'`.
18. Fill missing values in multiple columns simultaneously using a dictionary: `{'name': 'Unknown', 'age': 0, 'score': df['score'].mean()}`.
19. Forward-fill missing values down each column using `df.ffill()`.
20. Backward-fill missing values up each column using `df.bfill()`.
21. Forward-fill missing values with a maximum consecutive fill limit of `1` (`limit=1`).
22. Fill missing values in `'joined'` with a fixed timestamp `pd.Timestamp('2024-01-01')`.
23. Replace missing values in `'score'` only where `'age' > 30` using `.loc[]` and `.isna()`.
24. Use `df.combine_first(backup_df)` to patch missing values in `df` from a fallback `DataFrame`.
25. Drop column `'joined'` using `df.drop(columns=['joined'])` and remove `'id'` using `df.pop('id')`.


## Interpolation & Replacing Values

Use:
```python
sensor = pd.DataFrame({
    'time': pd.date_range('2026-01-01', periods=7, freq='h'),
    'temp': [20.0, np.nan, np.nan, 26.0, 28.0, np.nan, 32.0],
    'status': ['OK', 'ERR', 'ok', 'N/A', 'OK', 'missing', 'ERR']
})
```

26. Linearly interpolate missing `'temp'` values using `sensor['temp'].interpolate()`.
27. Interpolate `'temp'` using `'polynomial'` interpolation of `order=2`.
28. Interpolate `'temp'` using `'time'` method after setting `'time'` as the `DatetimeIndex`.
29. Interpolate missing values only in the forward direction up to 1 step (`limit=1, limit_direction='forward'`).
30. Replace sentinel strings `'N/A'` and `'missing'` in `'status'` with `np.nan` using `.replace()`.
31. Standardize `'status'` by replacing `'ok'` with `'OK'` and `'ERR'` with `'ERROR'` using a mapping dictionary in `.replace()`.
32. Replace values using regular expressions: `sensor['status'].replace(r'^ok$', 'OK', regex=True)`.
33. Map `'status'` codes `{'OK': 1, 'ERROR': 0}` into a new numeric column using `.map()` (and observe what happens to unmapped values).
34. Insert a new column `'unit'` with value `'C'` at column position 1 using `sensor.insert(1, 'unit', 'C')`.
35. Replace negative values in a numeric column with `np.nan` using `.mask()`.


## Duplicates, Structural Cleaning & Validation

Use:
```python
raw_users = pd.DataFrame({
    'email': ['a@x.com', 'b@x.com', 'a@x.com', 'c@x.com', 'b@x.com', 'd@x.com'],
    'signup_date': ['2025-01-01', '2025-01-02', '2025-01-05', '2025-01-03', '2025-01-02', '2025-01-04'],
    'tags': [['vip', 'beta'], ['free'], ['vip'], ['pro', 'beta'], ['free'], []]
})
```

36. Identify exact duplicate rows across all columns using `raw_users.duplicated()`.
37. Identify duplicate `'email'` entries keeping the first occurrence as `False` and subsequent ones as `True`.
38. Remove duplicate `'email'` rows while keeping the **last** occurrence (`keep='last'`).
39. Remove duplicates while keeping only rows that have no duplicates at all (`keep=False`).
40. Sort by `'signup_date'` descending and drop duplicate `'email'` entries so only the most recent signup per user remains.
41. Expand the list-valued `'tags'` column into separate rows using `raw_users.explode('tags')`.
42. Clean column names of a messy `DataFrame` by stripping whitespace, lowercasing, and replacing spaces with underscores.
43. Convert a 1-column `DataFrame` into a `Series` using `.squeeze()`.
44. Reset row numbering cleanly (`0, 1, 2, ...`) after dropping rows using `reset_index(drop=True)`.
45. Validate that `'email'` contains no `NaN` values and no duplicates using `assert` statements with `.notna().all()` and `.is_unique`.


## Challenge Questions: Real-World Data Hygiene

46. **Group-Wise Imputation**: Given a `DataFrame` with `'dept'` and `'salary'` (containing `NaN`), fill each missing salary with the median salary of its own `'dept'` using `groupby('dept')['salary'].transform('median')`.
47. **Group-Wise Forward Fill**: Given time-ordered sensor logs for multiple `device_id`s, forward-fill missing readings *within each device* without leaking values across devices.
48. **Mixed-Type Numeric Cleaning**: Given a dirty price column `['$1,200.50', '850.00', 'N/A', '$45.99', '--']`, strip currency symbols/commas and convert to `float64` with invalid entries coerced to `NaN`.
49. **Missingness Indicator Features**: Before imputing missing values in columns `['age', 'income']`, automatically create binary indicator columns `'age_is_missing'` and `'income_is_missing'`.
50. **Threshold Column Pruning**: Programmatically drop all columns from a `DataFrame` where more than 40% of the values are missing.

---

Try solving as many questions as possible using vectorized Pandas cleaning methods (`.isna()`, `.dropna()`, `.fillna()`, `.ffill()`, `.interpolate()`, `.replace()`, `.drop_duplicates()`, `.explode()`) without Python `for` loops.
