# Sorting, Ranking & Duplicates Question Bank Compiled by AutoMind Team

## Beginner: Basic Value & Index Sorting

Use this setup for Questions 1–10:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import pandas as pd                                        %
% import numpy as np                                         %
%                                                            %
% df = pd.DataFrame({                                        %
%     'name': ['Charlie', 'Alice', 'Bob', 'Diana', 'Evan'],  %
%     'dept': ['Eng', 'HR', 'Eng', 'Sales', 'HR'],           %
%     'age': [35, 28, 30, 41, 25],                           %
%     'salary': [120000, 75000, 95000, 88000, np.nan]        %
% }, index=[104, 101, 105, 102, 103])                        %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Sort `df` by `'age'` in ascending order using `df.sort_values('age')`.
2. Sort `df` by `'salary'` in descending order using `ascending=False`.
3. Sort `df` by `'salary'` while placing `NaN` values **first** instead of last using `na_position='first'`.
4. Sort `df` by `'dept'` ascending and then `'salary'` descending in a single `sort_values(['dept', 'salary'], ascending=[True, False])` call.
5. Sort `df` by its row index in ascending order using `df.sort_index()`.
6. Sort `df` columns alphabetically by column name using `df.sort_index(axis=1)`.
7. Sort `df` by `'name'` case-insensitively using `key=lambda s: s.str.lower()`.
8. Sort a `Series` `df['name']` by string length using `key=lambda s: s.str.len()`.
9. Sort `df` using a stable sorting algorithm (`kind='mergesort'` or `kind='stable'`) and explain when stability matters.
10. Verify whether `df.index` is sorted in ascending order using `df.index.is_monotonic_increasing`.


## Intermediate: Ranking & Top-K Selection

Use:
```python
scores = pd.DataFrame({
    'player': ['P1', 'P2', 'P3', 'P4', 'P5', 'P6'],
    'team': ['Red', 'Blue', 'Red', 'Blue', 'Red', 'Blue'],
    'points': [100, 85, 100, 90, 70, 85]
})
```

11. Compute the default (`method='average'`) rank of `'points'` in ascending order using `scores['points'].rank()`.
12. Rank `'points'` in descending order (`ascending=False`) so the highest score gets rank `1`.
13. Rank `'points'` using `method='min'` (standard competition ranking: `1, 1, 3`) vs `method='max'`.
14. Rank `'points'` using `method='dense'` so tied ranks do not skip numbers (`1, 1, 2`).
15. Rank `'points'` using `method='first'` to break ties by row appearance order.
16. Compute percentile ranks (`0.0` to `1.0`) of `'points'` using `pct=True`.
17. Rank `'points'` **within each `'team'`** using `scores.groupby('team')['points'].rank(ascending=False)`.
18. Extract the top 3 rows with the highest `'points'` using `scores.nlargest(3, 'points')`.
19. Handle ties in `nlargest` by keeping all tied rows using `keep='all'` vs keeping the last using `keep='last'`.
20. Extract the 2 rows with the smallest `'points'` using `scores.nsmallest(2, 'points')`.


## Uniqueness, Value Counts & Deduplication

Use:
```python
events = pd.DataFrame({
    'user': ['U1', 'U2', 'U1', 'U3', 'U2', 'U1', 'U4', np.nan],
    'action': ['login', 'click', 'login', 'view', 'click', 'buy', 'view', 'login'],
    'ts': [10, 20, 30, 40, 50, 60, 70, 80]
})
```

21. List all unique values in `'user'` (including `NaN`) using `events['user'].unique()`.
22. Count the number of unique non-null values in `'user'` using `.nunique()` and include `NaN` with `dropna=False`.
23. Compute frequency counts of `'action'` using `.value_counts()`, and normalize to proportions with `normalize=True`.
24. Compute `value_counts(dropna=False)` on `'user'` so missing values are included in the tally.
25. Compute `value_counts()` sorted in ascending order of frequency (`ascending=True`) or sorted by value (`sort_index()`).
26. Bin a numeric column `'ts'` into 4 equal-width intervals directly inside `value_counts(bins=4)`.
27. Compute joint frequency counts of `['user', 'action']` pairs using `events.value_counts(subset=['user', 'action'])`.
28. Detect duplicate rows across all columns using `events.duplicated()`.
29. Detect duplicates based only on `['user', 'action']` while marking **all** duplicates (including the first) as `True` (`keep=False`).
30. Drop duplicate `'user'` rows while keeping the **last** occurrence (`keep='last'`).
31. Drop rows that appear more than once (`keep=False`) to retain only strictly unique `'user'` entries.
32. Check whether `'ts'` has any duplicate values using `events['ts'].is_unique`.
33. Remove consecutive duplicate values in a `Series` `s` (e.g., `[1, 1, 2, 2, 2, 1] -> [1, 2, 1]`) using `s[s != s.shift()]`.
34. Sort `events` by `'ts'` descending and deduplicate by `'user'` to keep only each user's latest event.
35. Deduplicate a `DataFrame` in-place vs returning a new `DataFrame` with `reset_index(drop=True)`.


## Advanced Sorting & Custom Ordering

36. Sort a `DataFrame` by a custom non-alphabetical list order (e.g., `['High', 'Medium', 'Low']`) using `pd.Categorical(..., ordered=True)`.
37. Sort a `MultiIndex` `DataFrame` on only the second level (`level=1`) using `sort_index(level=1)`.
38. Sort a `DataFrame` by the frequency of values in a column `'action'` (most frequent categories first).
39. Find the indices that would sort a `Series` without modifying it (argsort equivalent) using `np.argsort(s.to_numpy())` or `s.sort_values().index`.
40. Check if a `Series` is strictly increasing (`is_monotonic_increasing` and `is_unique`).


## Challenge Questions: Sorting, Ranking & Deduplication Pipelines

41. **Multi-Criteria Tie-Breaking**: Sort `scores` by `'points'` descending, breaking ties by `'team'` ascending, and then `'player'` ascending.
42. **Dense Rank Top-N Filter**: Filter `scores` to keep all rows whose dense rank within `'team'` is `<= 2` (preserving ties).
43. **Pareto / 80-20 Cumulative Share**: Sort products by `'revenue'` descending, compute cumulative revenue percentage, and flag the top products contributing 80% of total revenue.
44. **Fuzzy / Case-Insensitive Deduplication**: Deduplicate emails `['Alice@x.com', 'alice@x.com', 'BOB@y.com']` case-insensitively while preserving the original casing of the first occurrence.
45. **Order-Preserving Unique**: Extract unique elements from a `Series` in order of first appearance (note: `s.unique()` preserves order in Pandas) and compare with `sorted(s.dropna().unique())`.
46. **Index-Aligned Rank Difference**: Compute the change in rank of each item between `month_1` and `month_2` (`rank_m2 - rank_m1`).
47. **Quantile Bucket Ranking**: Assign decile ranks (`1` to `10`) to a numeric `Series` using `pd.qcut(..., q=10, labels=range(1, 11))`.
48. **Fastest Latest-Row-Per-Key**: Compare `df.sort_values('ts').drop_duplicates('user', keep='last')` against `df.loc[df.groupby('user')['ts'].idxmax()]` on 100k rows.
49. **Run-Length Encoding (RLE)**: Compress consecutive identical values in a `Series` into `(value, run_length)` pairs using `(s != s.shift()).cumsum()` and `groupby`.
50. **Custom Natural Sort**: Sort strings `['item2', 'item10', 'item1', 'item20']` naturally (`item1, item2, item10, item20`) using `key=lambda s: s.str.extract(r'(\d+)')[0].astype(int)`.

---

Try solving as many questions as possible using `.sort_values()`, `.sort_index()`, `.rank()`, `.nlargest()`, `.value_counts()`, and `.drop_duplicates()` without Python `for` loops.
