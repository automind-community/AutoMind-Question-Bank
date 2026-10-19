# Aggregation Question Bank Compiled by AutoMind Team

## Beginner: 1D Aggregations

Use this array for Questions 1–10:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import numpy as np                                         %
%                                                            %
% arr = np.array([12, 45, 7, 23, 89, 34, 56, 12, 90, 3])     %
%                                                            %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Calculate the sum of all elements in `arr`.
2. Find the minimum and maximum values in `arr`.
3. Find the index of the minimum value in `arr` using `np.argmin()`.
4. Find the index of the maximum value in `arr` using `np.argmax()`.
5. Compute the arithmetic mean of `arr`.
6. Compute the median value of `arr`.
7. Compute the standard deviation and variance of `arr`.
8. Calculate the product of all elements in `arr`.
9. Compute the peak-to-peak range (max - min) of `arr` using `np.ptp()`.
10. Count the number of non-zero elements in `arr` using `np.count_nonzero()`.


## Intermediate: Statistical & Cumulative Aggregations

Use:
```python
arr = np.array([5, 10, 15, 20, 25, 30, 35, 40, 45, 50])
```

11. Compute the cumulative sum of `arr` using `np.cumsum()`.
12. Compute the cumulative product of `arr` using `np.cumprod()`.
13. Compute the 25th, 50th, and 75th percentiles (quartiles) of `arr`.
14. Compute the 0.90 quantile (90th percentile) of `arr` using `np.quantile()`.
15. Calculate the weighted average of `arr` given weights `w = np.arange(1, 11)` using `np.average()`.
16. Determine if **any** element in `arr` is greater than 40 using `np.any()`.
17. Determine if **all** elements in `arr` are positive using `np.all()`.
18. Count how many elements in `arr` are multiples of 10.
19. Compute the discrete differences between consecutive elements using `np.diff()`.
20. Calculate the sum of squared deviations from the mean: $\sum (x_i - \mu)^2$.


## 2D Array Aggregations: Along Axes

Use this array for Questions 21–35:

```python
matrix = np.array([
    [10, 25, 13, 44, 15],
    [36, 17, 88, 19, 20],
    [21, 62, 23, 14, 75],
    [46, 27, 38, 99, 30]
])
```

21. Compute the overall sum of all elements in `matrix`.
22. Compute the column-wise sum (`axis=0`), collapsing rows to produce a 1D array of 5 elements.
23. Compute the row-wise sum (`axis=1`), collapsing columns to produce a 1D array of 4 elements.
24. Compute the row-wise sum while retaining the 2D shape using `keepdims=True`.
25. Find the maximum value in each column.
26. Find the minimum value in each row.
27. Find the index of the maximum value along each column (`axis=0`).
28. Find the index of the maximum value along each row (`axis=1`).
29. Find the global maximum in `matrix` and convert its flat index to `(row, col)` coordinates using `np.unravel_index()`.
30. Calculate the mean of each column.
31. Calculate the sample standard deviation of each row using `ddof=1`.
32. Compute the cumulative sum along axis 0 (running sum down each column).
33. Compute the cumulative sum along axis 1 (running sum across each row).
34. Check if any row contains a value greater than 90 using `np.any(axis=1)`.
35. Count how many values exceed 30 in each column using boolean aggregation.


## Advanced & NaN-Aware Aggregations

Use this array containing missing values (`np.nan`):

```python
data = np.array([
    [ 5.0, np.nan, 12.0,  4.0],
    [np.nan, 10.0, 15.0, np.nan],
    [ 8.0,  3.0, np.nan, 20.0]
])
```

36. Calculate the sum of all valid (non-NaN) elements in `data` using `np.nansum()`.
37. Calculate the mean of each column ignoring NaNs using `np.nanmean(axis=0)`.
38. Calculate the median of each row ignoring NaNs using `np.nanmedian(axis=1)`.
39. Find the minimum value in each column ignoring NaNs using `np.nanmin()`.
40. Find the index of the minimum element in each column ignoring NaNs using `np.nanargmin(axis=0)`.
41. Compute the standard deviation of `data` ignoring NaNs using `np.nanstd()`.
42. Count the number of NaN values in each column of `data`.
43. Compute the percentage of missing values (NaNs) in the entire dataset.
44. Calculate the sum of only the positive elements in `x = np.array([-5, 10, -3, 8, -2, 7])`.
45. Compute the trimmed mean of an array by excluding the lowest 10% and highest 10% of values before averaging.


## 3D Array Aggregations

Use:
```python
tensor = np.arange(1, 25).reshape(2, 3, 4)

# tensor has shape (2, 3, 4)
```

46. Compute the global sum of all 24 elements in `tensor`.
47. Compute the mean across the depth slices (`axis=0`), resulting in a 2D array of shape `(3, 4)`.
48. Compute the sum across both axis 1 and axis 2 simultaneously using a tuple `axis=(1, 2)`, yielding shape `(2,)`.
49. Find the maximum value along the last axis (`axis=-1`) while keeping dimensions (`keepdims=True`).
50. Compute the index of the maximum value along axis 1 for each slice.


## Challenge Questions

51. **Frequency & Mode**: Find the most frequent element (mode) in `arr = np.array([1, 3, 2, 3, 4, 3, 2, 1, 3, 5])` using `np.unique(..., return_counts=True)` and `np.argmax()`.
52. **Top-K Largest Elements**: Find the 3 largest values in an unsorted array `vals = np.array([45, 12, 89, 34, 99, 23, 76])` efficiently using `np.partition()` or `np.argpartition()` without sorting the entire array.
53. **Grouped / Binned Sum**: Given group labels `groups = np.array([0, 1, 0, 2, 1, 2, 0])` and values `vals = np.array([10, 20, 30, 40, 50, 60, 70])`, calculate the sum of values for each group using `np.bincount()`.
54. **Moving Window Average**: Given a 1D time series `ts = np.array([2, 4, 6, 8, 10, 12, 14, 16])`, compute a rolling 3-period moving average using cumulative sums (`np.cumsum()`).
55. **Pairwise Correlation**: Compute the Pearson correlation coefficient between two 1D series `x` and `y` manually using NumPy aggregation functions (`np.mean`, `np.sum`, `np.std`) without calling `np.corrcoef`.

---

Try solving as many questions as possible using NumPy's built-in aggregation functions (e.g., `np.sum`, `np.mean`, `np.min`, `np.max`, `np.argmax`, `np.nansum`, `np.bincount`) and axis/dimension arguments (`axis=...`, `keepdims=True`) without using `for` loops.
