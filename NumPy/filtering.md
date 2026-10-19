# Filtering Question Bank Compiled by AutoMind Team

## Beginner: 1D Boolean Indexing & Basic Conditions

Use this array for Questions 1–20:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import numpy as np                                                               %
%                                                                                  %
% arr = np.array([12, -7, 45, 0, 23, -15, 88, 34, -3, 56, 12, 90, -22, 18, 5, 42]) %
%                                                                                  %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Extract all positive numbers (elements > 0) from `arr`.
2. Extract all negative numbers from `arr`.
3. Extract all zero elements from `arr`.
4. Extract all even numbers from `arr`.
5. Extract all odd numbers from `arr`.
6. Extract all numbers strictly greater than 40 from `arr`.
7. Extract all numbers less than or equal to 15 from `arr`.
8. Create and display a boolean mask of the same shape as `arr` where values are positive.
9. Count how many elements in `arr` are greater than 25 without extracting them.
10. Check if there are any negative numbers in `arr` using boolean masking and `np.any()`.
11. Check if all elements in `arr` are greater than -50 using `np.all()`.
12. Find the integer indices of all positive elements in `arr` using `np.where()`.
13. Find the indices of all non-zero elements using `np.nonzero()`.
14. Replace all negative numbers in `arr` with 0 in-place.
15. Replace all numbers greater than 50 with 999 without altering other values.
16. Extract all elements from `arr` that are multiples of 5.
17. Extract elements that are located at even index positions AND have positive values.
18. Find and extract all elements that are strictly greater than the mean of `arr`.
19. Find and extract all elements that are strictly less than the median of `arr`.
20. Invert a boolean condition `mask = (arr > 30)` using the bitwise NOT operator `~`.


## Intermediate: Compound Conditions & np.where

Use:
```python
arr = np.arange(-20, 21)
```

21. Extract numbers that are both strictly greater than 0 AND less than 15 using `&`.
22. Extract numbers that are either less than -10 OR greater than 10 using `|`.
23. Extract numbers that are positive but NOT divisible by 2 using `&` and `~`.
24. Extract numbers that are divisible by both 3 AND 5.
25. Extract numbers between -12 and 12 (inclusive) that are also odd.
26. Using `np.where()`, return an array with string `'Positive'` for elements > 0, and `'Non-Positive'` otherwise.
27. Using `np.where()`, square the numbers that are negative and keep non-negative numbers unchanged.
28. Using `np.where()`, double the numbers that are even and triple the numbers that are odd.
29. Replace values outside the range `[-8, 8]` with 0 using `np.where()`.
30. Clamp (clip) array values between -5 and 5 using `np.where()` without using `np.clip()`.
31. Using nested `np.where()`, label elements as `'Negative'`, `'Zero'`, or `'Positive'`.
32. Find all values in `arr` that fall within 1 standard deviation of the mean.
33. Find all values in `arr` that are statistical outliers (more than 2 standard deviations away from the mean).
34. Extract elements that satisfy an XOR condition: either divisible by 2 OR divisible by 3, but NOT both (`^`).
35. Extract all elements whose absolute value $|x|$ is strictly greater than 10.
36. Set all values divisible by 4 to -1 using boolean indexing.
37. Count the total number of elements that satisfy `(-10 <= arr) & (arr <= 10)`.
38. Extract all elements from `arr` that end with digit 5 or -5 (`np.abs(arr) % 10 == 5`).
39. Calculate the sum of only the positive values in `arr` using boolean masking.
40. Calculate the mean of only the negative odd numbers in `arr`.


## 2D Array Filtering: Row & Column Selection by Condition

Use this array for Questions 41–60:

```python
matrix = np.array([
    [ 12,  -4,  25,  18,   0],
    [-15,  30,  45,  -2,  60],
    [  7,  14, -21,  35,  28],
    [ 50,   0,  11, -99,  16],
    [ 22,  33,  44,  55,  66]
])
```

41. Extract all elements in `matrix` that are strictly greater than 20 into a 1D array.
42. Extract all negative elements from `matrix`.
43. Replace all negative values in `matrix` with 0 in-place.
44. Count how many total elements in `matrix` are positive.
45. Filter and extract entire rows where the first element (column 0) is greater than 10.
46. Filter and extract entire rows where the sum of the row exceeds 50.
47. Filter and extract rows that do NOT contain any negative numbers (`~np.any(matrix < 0, axis=1)`).
48. Filter and extract rows where at least one element is 0.
49. Filter and extract columns where the column sum is positive.
50. Filter and extract columns where every single element is an even number (`np.all(matrix % 2 == 0, axis=0)`).
51. Extract rows where the row mean is greater than the overall matrix mean.
52. Extract columns where the maximum value in that column exceeds 50.
53. Replace all elements in `matrix` smaller than the global median with the median value.
54. Set all negative elements in the first two rows to 0 without affecting other rows.
55. Get the `(row_idx, col_idx)` coordinates of all elements equal to 0 using `np.where()`.
56. Filter and retain only rows where the last element is greater than the first element.
57. In-place conditional update: multiply all positive entries by 2 and replace negative entries with -1.
58. Extract the sub-matrix formed by selecting rows that have at least three positive elements.
59. Extract the main diagonal elements of `matrix` that are strictly positive.
60. Find which row index contains the greatest number of negative elements.


## Advanced Filtering: np.select, np.isin, np.extract, & Membership

Use:
```python
data = np.array([10, 25, 40, 55, 70, 85, 100, 15, 30, 45, 60, 75, 90])
```

61. Extract elements from `data` that belong to the set `{15, 45, 75, 90}` using `np.isin()`.
62. Extract elements from `data` that DO NOT belong to `{10, 40, 70, 100}` using `~np.isin()`.
63. Using `np.extract()`, extract elements from `data` where `data % 6 == 0`.
64. Using `np.select()`, categorize values into `'Low'` (< 35), `'Medium'` (35–70), and `'High'` (> 70).
65. Using `np.select()`, map scores to letter grades: `>= 85: 'A'`, `>= 70: 'B'`, `>= 50: 'C'`, else: `'F'`.
66. Find the index positions of elements in `data` that match any element in `targets = np.array([25, 55, 85])`.
67. Given `words = np.array(['apple', 'banana', 'avocado', 'cherry', 'apricot'])`, filter words that start with `'a'`.
68. Filter elements in `data` that lie within the closed range `[30, 75]`.
69. Using `np.piecewise()`, apply $x^2$ for $x < 30$, $2x$ for $30 \le x \le 70$, and $x/2$ for $x > 70$.
70. Given two parallel arrays `scores` and `passed_flags`, filter `scores` where `passed_flags == True`.
71. Filter elements that appear only once (non-duplicated values) in an array with duplicate entries.
72. Filter out duplicate values while preserving their first occurrence order.
73. Filter elements of `data` that are strictly greater than their position index ($x_i > i$).
74. Find indices where two consecutive elements differ by more than 20.
75. Filter all elements in `data` whose reverse digits are identical (palindromic numbers).


## Missing, Infinite, & Special Float Filtering

Use this array containing missing and infinite values:

```python
raw = np.array([1.5, np.nan, 3.2, np.inf, -np.inf, 4.8, np.nan, 0.0, -2.1, 7.9])
```

76. Extract all non-NaN values from `raw` using `~np.isnan()`.
77. Extract all finite values from `raw` using `np.isfinite()`.
78. Count how many `NaN` values are present in `raw`.
79. Count how many infinite values (`+inf` or `-inf`) are in `raw` using `np.isinf()`.
80. Replace all `NaN` values in `raw` with 0.0 in-place.
81. Replace all infinite values in `raw` with the maximum finite value in the array.
82. Replace all `NaN` values with the arithmetic mean of all finite values in `raw`.
83. Given a 2D matrix, filter and drop any row that contains at least one `NaN`.
84. Given a 2D matrix, filter and drop any column that contains at least one `NaN`.
85. In a 2D matrix, replace `NaN` values in each column with that column's mean (imputation).


## 3D Array Filtering & Dimension-Preserving Masking

Use:
```python
tensor = np.arange(-12, 12).reshape(2, 3, 4)

# tensor has shape (2, 3, 4)
```

86. Extract all positive values from `tensor` into a flat 1D array.
87. Replace all negative values in `tensor` with 0 while preserving the 3D shape `(2, 3, 4)`.
88. Filter and select only the 2D matrices (along axis 0) whose overall sum is positive.
89. Find the 3D coordinate tuples `(depth, row, col)` of all elements greater than 5 using `np.argwhere()`.
90. Zero-out all elements in `tensor` that fall outside the range `[-6, 6]` without modifying array shape.
91. Extract slices along axis 1 where all elements along axis 2 are positive.
92. Apply a 2D boolean mask of shape `(3, 4)` to filter both slices of `tensor` simultaneously.


## Challenge Questions: Real-World Filtering & Outlier Removal

93. **IQR Outlier Filtering**: Given a 1D dataset `x`, filter out all values below $Q_1 - 1.5 \times \text{IQR}$ or above $Q_3 + 1.5 \times \text{IQR}$.
94. **Z-Score Filtering**: Filter and keep only data points whose absolute standard score satisfies $|Z| \le 3$.
95. **Top-N Percentage Filtering**: Filter and extract only the top 10% highest values from an unsorted dataset.
96. **Conditional Non-Zero Compression**: Extract all non-zero elements from an array and pad the end with zeros to preserve the original length.
97. **Zero-Crossing Detection**: Find the indices where a 1D signal changes sign (crosses zero: `arr[:-1] * arr[1:] < 0`).
98. **Consecutive Duplicate Removal**: Filter out adjacent repeated elements in a 1D array using boolean masking (`arr[1:] != arr[:-1]`).
99. **Masked Row-wise Aggregation**: Given a 2D matrix, calculate the mean of only positive numbers for each row (ignoring negatives and zeros).
100. **Multi-Condition Co-occurrence**: Given a 2D feature matrix `X` of shape `(N, D)`, filter and keep rows that have fewer than 2 zero-valued features.

---

Try solving as many questions as possible using vectorized boolean indexing (`arr[condition]`), logical bitwise operators (`&`, `|`, `~`, `^`), and conditional filtering functions (`np.where`, `np.select`, `np.isin`, `np.isnan`, `np.isfinite`) without using Python `for` loops.
