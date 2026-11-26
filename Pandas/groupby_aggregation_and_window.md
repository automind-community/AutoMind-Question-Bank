# GroupBy, Aggregation & Window Functions Question Bank Compiled by AutoMind Team

## Beginner: Basic GroupBy & Aggregations

Use this setup for Questions 1–10:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import pandas as pd                                        %
% import numpy as np                                         %
%                                                            %
% sales = pd.DataFrame({                                     %
%     'region': ['East', 'West', 'East', 'North', 'West',    %
%                'North', 'East', 'West'],                   %
%     'rep': ['Alice', 'Bob', 'Alice', 'Cara', 'Bob',        %
%             'Dan', 'Eve', 'Bob'],                          %
%     'category': ['Tech', 'Tech', 'Office', 'Tech',         %
%                  'Office', 'Office', 'Tech', 'Tech'],      %
%     'revenue': [1200, 850, 300, 1500, 400, 250, 950, 1100],%
%     'units': [4, 3, 10, 5, 12, 8, 3, 4]                    %
% })                                                         %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Group `sales` by `'region'` and calculate the total `'revenue'` for each region.
2. Group `sales` by `'region'` and calculate the mean `'revenue'` and `'units'`.
3. Count the number of rows (transactions) per `'region'` using `.size()` vs `.count()`.
4. Count the number of unique sales reps (`'rep'`) in each `'region'` using `.nunique()`.
5. Group by multiple columns `['region', 'category']` and compute the sum of `'revenue'`.
6. Group by `['region', 'category']` with `as_index=False` so grouping keys remain regular columns.
7. Retrieve the first and last transaction in each `'region'` using `.first()` and `.last()`.
8. Retrieve the 2nd row (`nth(1)`) of each `'region'` group using `.nth(1)`.
9. Inspect the dictionary mapping group names to row indices using `.groups` and extract only the `'East'` group using `.get_group('East')`.
10. Group by `'region'` and include `NaN` keys (if any exist) by setting `dropna=False`.


## Intermediate: Named Aggregations, Transform & Filter

Use the same `sales` DataFrame for Questions 11–25:

11. Compute `min`, `max`, and `mean` of `'revenue'` per `'region'` in a single `.agg(['min', 'max', 'mean'])` call.
12. Apply different aggregations to different columns using a dict: `.agg({'revenue': ['sum', 'mean'], 'units': 'max'})`.
13. Use **named aggregation** (`.agg(total_rev=('revenue', 'sum'), avg_units=('units', 'mean'))`) to produce clean flat column names.
14. Pass a custom lambda function to `.agg()` to compute the range (`max - min`) of `'revenue'` per `'region'`.
15. Use `.transform('sum')` to add a new column `'region_total_rev'` containing each row's regional total revenue (same length as `sales`).
16. Calculate each transaction's percentage share of its region's total revenue using `sales['revenue'] / sales.groupby('region')['revenue'].transform('sum')`.
17. Demean `'revenue'` within each `'region'` (`x - x.mean()`) using `.transform()`.
18. Filter `sales` to keep only regions whose total revenue exceeds `2000` using `groupby('region').filter(...)`.
19. Filter `sales` to keep only reps who have made at least 2 transactions using `groupby('rep').filter()`.
20. Use `groupby().apply()` to return the top 2 highest-revenue rows for each `'region'` (and understand `include_groups=False` in modern Pandas).
21. Compute cumulative sum of `'revenue'` within each `'rep'` using `groupby('rep')['revenue'].cumsum()`.
22. Assign a sequential transaction number (`0, 1, 2, ...`) within each `'region'` using `groupby('region').cumcount()`.
23. Rank transactions by `'revenue'` within each `'region'` using `groupby('region')['revenue'].rank(ascending=False)`.
24. Compute a global summary row/column on a numeric DataFrame using `.agg(['sum', 'mean', 'std'])` across `axis=0` and `axis=1`.
25. Group a `Series` by an external array/list of group labels of the same length (without adding it as a column).


## Rolling, Expanding & Exponentially Weighted Windows

Use this time-ordered DataFrame for Questions 26–40:

```python
ts = pd.DataFrame({
    'date': pd.date_range('2026-01-01', periods=10, freq='D'),
    'price': [100, 102, 101, 105, 107, 106, 110, 112, 111, 115],
    'volume': [200, 220, 180, 300, 280, 210, 350, 400, 290, 420]
}).set_index('date')
```

26. Compute a 3-day simple moving average (SMA) of `'price'` using `.rolling(3).mean()`.
27. Compute a 3-day rolling sum of `'volume'` with `min_periods=1` so the first two days are not `NaN`.
28. Compute a centered 3-day rolling mean using `center=True`.
29. Compute a time-based 3-day rolling mean using an offset string `.rolling('3D').mean()` (works even with irregular timestamps).
30. Compute rolling standard deviation and rolling max/min simultaneously using `.rolling(4).agg(['mean', 'std', 'min', 'max'])`.
31. Compute the expanding (cumulative) mean and expanding max of `'price'` using `.expanding().mean()` and `.expanding().max()`.
32. Compute an exponentially weighted moving average (EWMA) of `'price'` with `span=4` using `.ewm(span=4).mean()`.
33. Compute the daily price change (`price_t - price_{t-1}`) using `.diff(1)` and daily percentage return using `.pct_change()`.
34. Shift `'price'` forward by 1 day (`lag_1`) and backward by 1 day (`lead_1`) using `.shift(1)` and `.shift(-1)`.
35. Compute a rolling 4-day correlation between `'price'` and `'volume'` using `ts['price'].rolling(4).corr(ts['volume'])`.
36. Apply a custom NumPy function to a rolling window using `.rolling(3).apply(..., raw=True)` for faster execution.
37. Compute a weighted moving average over a 3-day window with weights `[0.2, 0.3, 0.5]`.
38. Use `.rolling(3, win_type='gaussian').mean(std=1)` to compute a Gaussian-weighted rolling average.
39. Compute a rolling calculation **within each group** using `df.groupby('ticker')['price'].rolling(3).mean()`.
40. Compute a 5-day rolling quantile (e.g., 90th percentile) using `.rolling(5).quantile(0.9)`.


## Advanced GroupBy Patterns & Performance

41. Explain why `groupby(..., sort=False)` can speed up grouping on large DataFrames when group order does not matter.
42. Group a `DataFrame` by a function applied to its index (e.g., `df.groupby(df.index.day_name())`).
43. Group by binned ranges created on the fly with `pd.cut(sales['revenue'], bins=3)`.
44. Compute multiple percentiles (25th, 50th, 75th) per group cleanly without returning a MultiIndex row structure.
45. Describe the difference between `.groupby().agg()`, `.groupby().transform()`, and `.groupby().apply()` in terms of input/output shapes.


## Challenge Questions: Analytical & Window Pipelines

46. **Group-Wise Z-Score Normalization**: Standardize `'revenue'` within each `'region'` ($z = (x - \mu) / \sigma$) using `groupby` and `transform`.
47. **Volume-Weighted Average Price (VWAP)**: Compute a 5-day rolling VWAP: $\frac{\sum (\text{price} \times \text{volume})}{\sum \text{volume}}$ over a 5-day window.
48. **Sessionization by Gap**: Given user event timestamps, start a new session ID whenever the gap between consecutive events for a user exceeds 30 minutes using `groupby`, `diff()`, and `cumsum()`.
49. **Streak Counter**: Given a binary `win` column (`1` or `0`), compute the length of the current consecutive winning streak at each row using `groupby` and `cumsum()`.
50. **Drawdown Calculation**: Using `.expanding().max()`, compute the running maximum price and percentage drawdown `(price - peak) / peak` at every point in `ts`.


## Extended Practice: Advanced GroupBy & Window Patterns

51. Use `groupby('region', group_keys=False).apply(...)` and explain how `group_keys=False` prevents adding the grouping key to the result's index.
52. Count the number of `NaN` values per `'region'` inside a `groupby` using `.apply(lambda g: g.isna().sum())` or `df['col'].isna().groupby(df['region']).sum()`.
53. Compute the percentage of rows where `revenue > 1000` within each `'region'` using `(sales['revenue'] > 1000).groupby(sales['region']).mean() * 100`.
54. Compute multiple named aggregations on the same column (`rev_sum`, `rev_median`, `rev_p90`) using a custom percentile function inside `.agg()`.
55. Iterate over `for name, group in sales.groupby('region'):` and explain when iteration is acceptable (e.g., writing per-group files) vs when `.agg()`/`.transform()` should be used.
56. Use `.rolling(5, closed='left').mean()` so the current row is excluded from its own rolling window (preventing data leakage in ML features).
57. Compute a rolling sum over a categorical/integer index using `on='date'` inside `df.rolling('7D', on='date').sum()`.
58. Compute an exponentially weighted standard deviation using `.ewm(alpha=0.3).std()`.
59. Compute an expanding count of non-null observations using `.expanding().count()`.
60. Compute `groupby('region').nth([-1, 0])` to select both the first and last row of each group.
61. Compute `groupby('region').head(1)` vs `groupby('region').first()` and explain how they differ when `NaN` values are present.
62. Use `groupby('region')['revenue'].nlargest(2)` to get the top 2 revenues per region.
63. Compute the difference between each row's `'revenue'` and the previous row's `'revenue'` **within each `'rep'`** using `groupby('rep')['revenue'].diff()`.
64. Compute the percentage change within each `'rep'` using `groupby('rep')['revenue'].pct_change()`.
65. Group by a `pd.Grouper(freq='ME')` on a `DatetimeIndex` and compute monthly aggregates without creating a helper `'month'` column.
66. Compute a 2D rolling correlation matrix across all numeric columns using `ts.rolling(5).corr()`.
67. Compute a 2D rolling covariance matrix between two DataFrames using `df1.rolling(5).cov(df2)`.
68. Use `groupby(..., observed=True)` on a `Categorical` column and explain why `observed=True` is recommended for memory and speed.
69. Compute the mode (most frequent value) of `'category'` within each `'region'` using `groupby('region')['category'].agg(lambda x: x.mode().iloc[0])`.
70. Compute a cumulative maximum (`cummax`) within each group using `groupby('region')['revenue'].cummax()`.


## Additional Challenge Questions

71. **Leak-Free Expanding Target Encoding**: For each row in a time-ordered dataset, compute the historical mean of `'target'` for its `'category'` strictly *prior* to the current row using `groupby('category')['target'].expanding().mean().shift(1)`.
72. **Weighted Group Average**: Compute the unit-weighted average revenue $\frac{\sum (\text{revenue} \times \text{units})}{\sum \text{units}}$ per `'region'` without using slow `groupby.apply()`.
73. **Rolling Beta (Financial)**: Given stock returns `r_stock` and market returns `r_mkt`, compute a 20-day rolling beta $\frac{\text{Cov}(r_{\text{stock}}, r_{\text{mkt}})}{\text{Var}(r_{\text{mkt}})}$ using `.rolling(20).cov()` and `.rolling(20).var()`.
74. **Gap-Free Group Resampling**: Given irregular timestamps per `'device_id'`, resample each device to `'1h'` frequency and forward-fill up to 2 hours using `groupby('device_id').resample('1h').ffill(limit=2)`.
75. **Group-Wise Winsorization**: Clip `'revenue'` within each `'region'` to its own `[5th, 95th]` percentile bounds using `groupby('region')['revenue'].transform(...)`.

---

Try solving as many questions as possible using `.groupby()`, `.agg()`, `.transform()`, `.rolling()`, `.expanding()`, `.ewm()`, `.shift()`, and `.pct_change()` without Python `for` loops.
