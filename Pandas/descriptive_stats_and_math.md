# Descriptive Statistics & Math Operations Question Bank Compiled by AutoMind Team

## Beginner: Basic Summary Statistics

Use this setup for Questions 1–10:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import pandas as pd                                        %
% import numpy as np                                         %
%                                                            %
% df = pd.DataFrame({                                        %
%     'A': [10, 20, 30, 40, 50],                             %
%     'B': [15, 25, 35, 45, 55],                             %
%     'C': [100, 80, 60, 40, 20]                             %
% }, index=['r1', 'r2', 'r3', 'r4', 'r5'])                   %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Compute the sum of each column (`axis=0`) and each row (`axis=1`) using `df.sum()`.
2. Compute the arithmetic mean and median of each column using `df.mean()` and `df.median()`.
3. Compute the sample standard deviation (`ddof=1`) and population standard deviation (`ddof=0`) using `df.std()`.
4. Compute the variance of each column using `df.var()`.
5. Find the minimum and maximum values of each column using `df.min()` and `df.max()`.
6. Find the index label of the minimum and maximum in each column using `df.idxmin()` and `df.idxmax()`.
7. Count non-null values in each column and each row using `df.count()`.
8. Compute custom percentiles `[0.1, 0.25, 0.5, 0.75, 0.9]` for all columns using `df.quantile()`.
9. Generate summary statistics for specific percentiles `df.describe(percentiles=[0.05, 0.5, 0.95])`.
10. Compute the mode (most frequent value) of each column using `df.mode()`.


## Intermediate: Vectorized Arithmetic, Alignment & Broadcasting

Use:
```python
df1 = pd.DataFrame({'x': [10, 20, 30], 'y': [4, 5, 6]}, index=['a', 'b', 'c'])
df2 = pd.DataFrame({'x': [2, 4, 6], 'z': [1, 2, 3]}, index=['b', 'c', 'd'])
row_vec = pd.Series({'x': 10, 'y': 2})
col_vec = pd.Series([1, 2, 3], index=['a', 'b', 'c'])
```

11. Add `df1` and `df2` using `df1.add(df2, fill_value=0)` and compare with `df1 + df2`.
12. Subtract `row_vec` from every row of `df1` using `df1.sub(row_vec, axis='columns')`.
13. Multiply every column of `df1` by `col_vec` using `df1.mul(col_vec, axis='index')`.
14. Perform true division (`div`), floor division (`floordiv`), and modulo (`mod`) on `df1` by `2`.
15. Raise every element of `df1` to the power of `2` using `df1.pow(2)` (or `df1 ** 2`).
16. Compute the dot product (matrix multiplication) of `df1` and `df1.T` using `df1.dot(df1.T)` (or `@`).
17. Compute the weighted sum of columns `'x'` and `'y'` with weights `pd.Series({'x': 0.7, 'y': 0.3})` using `.mul()` and `.sum(axis=1)`.
18. Round all float values in a `DataFrame` to 2 decimal places using `.round(2)`, and round different columns to different precisions using `.round({'x': 1, 'y': 3})`.
19. Compute element-wise absolute values using `.abs()` and clip values to `[5, 25]` using `.clip(5, 25)`.
20. Compare two DataFrames element-wise using `.eq()`, `.ne()`, `.gt()`, `.lt()`, `.ge()`, `.le()`.


## Cumulative, Difference & Distribution Metrics

Use:
```python
metrics = pd.DataFrame({
    'sales': [100, 120, 115, 140, 160, 155, 180],
    'costs': [70, 75, 80, 85, 90, 95, 100],
    'ads':   [10, 15, 12, 20, 25, 22, 30]
})
```

21. Compute the cumulative sum (`cumsum`) and cumulative product (`cumprod`) down each column.
22. Compute the running maximum (`cummax`) and running minimum (`cummin`) of `'sales'`.
23. Compute first-order differences (`diff(1)`) and second-order differences (`diff(1).diff(1)`) of `'sales'`.
24. Compute period-over-period percentage change using `metrics.pct_change()`.
25. Compute the skewness (`skew()`) and excess kurtosis (`kurt()`) of each numeric column.
26. Compute the Mean Absolute Deviation (MAD) manually via `(metrics - metrics.mean()).abs().mean()`.
27. Compute the Interquartile Range (IQR) for each column using `quantile(0.75) - quantile(0.25)`.
28. Compute the geometric mean of a positive `Series` `s` using `np.exp(np.log(s).mean())`.
29. Compute the harmonic mean of a positive `Series` `s` using `len(s) / (1 / s).sum()`.
30. Compute the coefficient of variation (`std / mean`) for each column.


## Correlation, Covariance & Cross-Series Analysis

Use the same `metrics` DataFrame for Questions 31–40:

31. Compute the pairwise Pearson correlation matrix using `metrics.corr()`.
32. Compute Spearman rank correlation (`method='spearman'`) and Kendall tau (`method='kendall'`).
33. Compute the pairwise covariance matrix using `metrics.cov()`.
34. Compute the correlation between `'sales'` and every other column using `metrics.corrwith(metrics['sales'])`.
35. Compute the correlation between two aligned DataFrames column-by-column using `df_a.corrwith(df_b)`.
36. Compute the correlation between `'sales'` and a 1-period lagged `'ads'` (`metrics['ads'].shift(1)`).
37. Find the pair of distinct columns with the highest absolute correlation in `metrics.corr()`.
38. Compute a correlation matrix while excluding pairs with fewer than 5 valid observations (`min_periods=5`).
39. Compute a weighted average of `'sales'` weighted by `'ads'` using `(metrics['sales'] * metrics['ads']).sum() / metrics['ads'].sum()`.
40. Standardize all columns in `metrics` to Z-scores: `(metrics - metrics.mean()) / metrics.std()`.


## Advanced Mathematical & Statistical Transformations

41. Normalize all columns in `metrics` to `[0, 1]` using min-max scaling: `(df - df.min()) / (df.max() - df.min())`.
42. Normalize each row of a `DataFrame` so that every row sums to `1.0` using `df.div(df.sum(axis=1), axis=0)`.
43. Apply a log1p transformation (`np.log1p(df)`) to right-skewed positive columns.
44. Compute Euclidean distance between every row of `df` and a reference vector `v` using `np.sqrt(((df - v) ** 2).sum(axis=1))`.
45. Compute cosine similarity between two `Series` `u` and `v` using `.dot()`, `np.linalg.norm()`, and `.to_numpy()`.


## Challenge Questions: Quantitative & Statistical Pipelines

46. **Compound Annual Growth Rate (CAGR)**: Given a `Series` of annual revenues over $N$ years, compute CAGR $= (V_{\text{end}} / V_{\text{start}})^{1/(N-1)} - 1$.
47. **Sharpe Ratio**: Given daily portfolio returns `r` and risk-free rate `rf = 0.0`, compute the annualized Sharpe ratio $\sqrt{252} \times \frac{\text{mean}(r)}{\text{std}(r)}$.
48. **Correlation Matrix Upper-Triangle Filter**: Extract all column pairs from `df.corr()` with $|r| > 0.85$ (excluding self-correlations) using `np.triu()` and `.stack()`.
49. **Robust Z-Score (MAD-based)**: Standardize a `Series` using median and Median Absolute Deviation: $0.6745 \times (x - \text{median}) / \text{median}(|x - \text{median}|)$.
50. **Weighted Quantile**: Compute the 50th percentile (weighted median) of values `v` with weights `w` using cumulative sorted weights without external libraries.

---

Try solving as many questions as possible using Pandas' built-in statistical and arithmetic methods (`.add()`, `.sub()`, `.mul()`, `.div()`, `.corr()`, `.cov()`, `.quantile()`, `.pct_change()`, `.cumsum()`) without Python `for` loops.
