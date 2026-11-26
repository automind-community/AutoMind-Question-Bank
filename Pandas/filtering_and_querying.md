# Filtering & Querying Question Bank Compiled by AutoMind Team

## Beginner: Boolean Indexing & Basic Conditions

Use this setup for Questions 1–10:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import pandas as pd                                        %
% import numpy as np                                         %
%                                                            %
% df = pd.DataFrame({                                        %
%     'emp': ['Alice', 'Bob', 'Charlie', 'Diana', 'Evan',    %
%             'Fiona', 'George', 'Hannah'],                  %
%     'dept': ['Eng', 'HR', 'Eng', 'Sales', 'HR',            %
%              'Sales', 'Eng', 'Finance'],                   %
%     'age': [28, 35, 42, 31, 24, 38, 45, 29],               %
%     'salary': [90000, 65000, 120000, 78000, 52000,         %
%                83000, 135000, 72000],                      %
%     'remote': [True, False, True, False, True,             %
%                True, False, False]                         %
% })                                                         %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Filter all rows where `salary` is strictly greater than `80000`.
2. Filter all rows where `dept` is equal to `'Eng'`.
3. Filter all rows where `remote` is `True` (without writing `== True`).
4. Filter all rows where `age` is less than or equal to `30`.
5. Filter all rows where `dept` is NOT `'HR'`.
6. Create a boolean `Series` mask for `salary >= 90000` and count how many rows match using `.sum()`.
7. Check if **any** employee earns more than `130000` using `.any()`.
8. Check if **all** employees are at least `21` years old using `.all()`.
9. Filter rows where `age` is between `28` and `38` (inclusive) using `.between(28, 38)`.
10. Filter rows where `dept` is in `['Eng', 'Finance']` using `.isin()`.


## Intermediate: Compound Conditions, Negation & .query()

Use the same `df` for Questions 11–25:

11. Filter employees in `'Eng'` who earn more than `100000` using `&`.
12. Filter employees who are either in `'HR'` OR work `remote` using `|`.
13. Filter employees who are NOT in `['HR', 'Sales']` using `~` and `.isin()`.
14. Filter employees in `'Sales'` OR `'Eng'` whose `age` is under `35` (ensure proper operator precedence with parentheses).
15. Filter employees whose `salary` is strictly above the mean salary of `df`.
16. Rewrite Question 11 (`dept == 'Eng'` and `salary > 100000`) using `df.query()`.
17. Use `df.query()` with an external Python variable `min_sal = 75000` using the `@min_sal` syntax.
18. Use `df.query()` to filter rows where `dept` is in a Python list `target_depts = ['Eng', 'Sales']`.
19. Use `df.query()` to find rows where `salary / age > 2800`.
20. Filter rows where `emp` starts with `'A'` or `'D'` using `.str.startswith(('A', 'D'))`.
21. Filter rows where `emp` contains the substring `'an'` (case-insensitive) using `.str.contains()`.
22. Filter rows where `age` is outside the range `[28, 40]` using `~df['age'].between(28, 40)`.
23. Filter rows using an exclusive-OR (`^`) condition: either `remote` is `True` OR `salary > 100000`, but not both.
24. Select only columns whose names contain `'a'` (like `'age'`, `'salary'`) using `df.filter(like='a')`.
25. Select columns matching the regex `'^(emp|dept)$'` using `df.filter(regex=...)`.


## Conditional Replacement: where, mask & clip

Use:
```python
scores = pd.DataFrame({
    'math': [88, 45, 92, 67, 30, 100],
    'physics': [76, 55, 89, 40, 95, 81],
    'chem': [60, 72, 38, 85, 50, 90]
}, index=['S1', 'S2', 'S3', 'S4', 'S5', 'S6'])
```

26. Keep values in `scores` where `scores >= 60` and replace all others with `np.nan` using `scores.where()`.
27. Replace all values in `scores` that are `< 50` with `50` (flooring failing scores) using `scores.mask(scores < 50, 50)`.
28. Clamp all values in `scores` to the range `[50, 95]` using `scores.clip(lower=50, upper=95)`.
29. Using `scores.where()`, replace values below each column's mean with that column's mean.
30. Filter `scores` to keep only rows where **all** three subjects have scores `>= 50`.
31. Filter `scores` to keep rows where **at least one** subject has a score `>= 95`.
32. Filter `scores` to keep columns whose column average is strictly greater than `70`.
33. Replace values in `'math'` with `'Pass'` if `>= 60` else `'Fail'` using `np.where()`.
34. Categorize `'math'` scores into `'Low'` (< 50), `'Mid'` (50–80), and `'High'` (> 80) using `np.select()`.
35. Bin `'physics'` scores into 3 labeled intervals `['Low', 'Medium', 'High']` using `pd.cut()`.


## Ranking, Extremes & Uniqueness

Use:
```python
orders = pd.DataFrame({
    'order_id': [101, 102, 103, 104, 105, 106, 107],
    'customer': ['C1', 'C2', 'C1', 'C3', 'C2', 'C1', 'C4'],
    'amount': [250.0, 120.0, 250.0, 980.0, 430.0, 75.0, 510.0],
    'status': ['paid', 'pending', 'paid', 'paid', 'cancelled', 'paid', 'paid']
})
```

36. Find the top 3 largest orders by `'amount'` using `orders.nlargest(3, 'amount')`.
37. Find the 2 smallest orders by `'amount'` using `orders.nsmallest(2, 'amount')`.
38. Find the index label of the single highest `'amount'` using `.idxmax()` and retrieve the full row with `.loc[]`.
39. Find the index label of the single lowest `'amount'` using `.idxmin()`.
40. Rank `'amount'` in descending order (`ascending=False`) with dense ranking (`method='dense'`).
41. Identify duplicate rows based on `['customer', 'amount']` using `orders.duplicated()`.
42. Extract all rows that appear more than once for the same `'customer'` using `orders.duplicated(subset=['customer'], keep=False)`.
43. Filter out duplicate `'customer'` rows, keeping only their most recent (last) order.
44. Count unique values in `'customer'` using `.nunique()` and list them using `.unique()`.
45. Compute the frequency distribution of `'status'` (including proportions via `normalize=True`) using `.value_counts()`.


## Challenge Questions: Statistical & Multi-Condition Filtering

46. **IQR Outlier Removal**: Given a numeric `Series` `s`, filter out outliers below $Q_1 - 1.5 \times \text{IQR}$ or above $Q_3 + 1.5 \times \text{IQR}$ using `.quantile()`.
47. **Z-Score Filtering**: Filter a `DataFrame` to retain only rows where all numeric columns have absolute Z-score $|Z| \le 2.5$.
48. **Top-K Per Group Filtering**: Without using `apply`, filter `orders` to keep only the top 2 highest `'amount'` rows per `'customer'` using `sort_values()` and `groupby().head(2)`.
49. **Dynamic Column-Name Querying**: Filter a `DataFrame` with a column named `'total cost ($)'` (containing spaces and symbols) inside `df.query()` using backticks `` `total cost ($)` > 100 ``.
50. **All-Condition Filtering with `eval`**: Use `df.eval()` to compute a boolean mask `high_value = (amount > 200) & (status == 'paid')` and filter `orders` with it in one expression.

---

Try solving as many questions as possible using vectorized boolean indexing, `.isin()`, `.between()`, `.query()`, `.where()`, `.nlargest()`, and `.idxmax()` without Python `for` loops.
