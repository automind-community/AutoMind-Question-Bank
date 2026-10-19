# Sorting, Searching & Counting Question Bank Compiled by AutoMind Team

## Beginner: 1D Sorting & Basic Searching

Use this setup for Questions 1–20:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import numpy as np                                         %
%                                                            %
% arr = np.array([42, 15, 88, 23, 7, 56, 15, 99, 34, 12])     %
%                                                            %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Sort array `arr` in ascending order returning a new array using `np.sort()`.
2. Sort array `arr` in-place using `.sort()`.
3. Sort array `arr` in descending order using slicing on the sorted result.
4. Obtain the indices that would sort `arr` in ascending order using `np.argsort()`.
5. Reconstruct the sorted array by indexing `arr` with its `np.argsort()` indices.
6. Obtain the indices that would sort `arr` in descending order.
7. Find the index of the first occurrence of the minimum value in `arr` using `np.argmin()`.
8. Find the index of the first occurrence of the maximum value in `arr` using `np.argmax()`.
9. Find the indices of all elements equal to 15 using `np.where()`.
10. Find the indices of all non-zero elements in `arr` using `np.nonzero()`.
11. Count the total number of non-zero elements in `arr` using `np.count_nonzero()`.
12. Check if the element 88 exists in `arr` using `np.isin()`.
13. Find the unique elements of `arr` in sorted order using `np.unique()`.
14. Count the frequency of each unique element in `arr` using `return_counts=True` in `np.unique()`.
15. Find the indices of the first occurrences of unique elements using `return_index=True`.
16. Reconstruct the original array from unique values and indices using `return_inverse=True`.
17. Check if `arr` is already sorted in ascending order using `np.all(np.diff(arr) >= 0)`.
18. Find the index where value 25 should be inserted to maintain sorted order in a sorted array using `np.searchsorted()`.
19. Find insertion indices with `side='right'` versus `side='left'` for duplicate values using `np.searchsorted()`.
20. Check whether an array contains any duplicates using `len(np.unique(arr)) < len(arr)`.


## Intermediate: 2D Sorting Along Axes & Lexsort

Use:
```python
mat = np.array([
    [12, 45, 23,  9],
    [34, 11, 88, 15],
    [56, 78, 14, 62]
])
```

21. Sort each row of `mat` independently in ascending order using `np.sort(mat, axis=1)`.
22. Sort each column of `mat` independently in ascending order using `np.sort(mat, axis=0)`.
23. Sort each row of `mat` in descending order along axis 1.
24. Obtain the sorting indices along rows using `np.argsort(mat, axis=1)`.
25. Obtain the sorting indices along columns using `np.argsort(mat, axis=0)`.
26. Sort the rows of `mat` based on the values in the first column (column 0).
27. Sort the rows of `mat` based on the values in the last column.
28. Sort the columns of `mat` based on the values in the first row.
29. Sort the rows of `mat` by row sums in ascending order.
30. Perform multi-key sorting on two columns (e.g., sort by column 0, then by column 1) using `np.lexsort()`.
31. Given `last_names = np.array(['Smith', 'Jones', 'Smith', 'Adams'])` and `first_names = np.array(['John', 'Bob', 'Alice', 'Charlie'])`, sort names by last name, then first name using `np.lexsort()`.
32. Flatten `mat`, sort all its elements, and reshape it back to the original shape `(3, 4)`.
33. Find the global minimum and maximum indices in `mat` and convert them to 2D coordinates `(row, col)` using `np.unravel_index()`.
34. Find the row and column coordinates where `mat > 50` using `np.argwhere()`.
35. Count how many elements in each row are greater than 20 using `np.count_nonzero(mat > 20, axis=1)`.
36. Count how many elements in each column are even numbers using `np.count_nonzero()`.
37. Find the unique rows of a 2D matrix using `np.unique(mat, axis=0)`.
38. Find the unique columns of a 2D matrix using `np.unique(mat, axis=1)`.
39. Sort complex numbers based on their absolute values using `np.argsort(np.abs(z))`.
40. Sort strings alphabetically ignoring case using `np.argsort(np.char.lower(str_arr))`.


## Partitioning & Fast Selection (Top-K Elements)

Use:
```python
vals = np.array([55, 12, 89, 34, 99, 23, 76, 45, 67, 10, 81, 19])
```

41. Partition `vals` so that the 3 smallest elements appear before index 3 using `np.partition(vals, 3)`.
42. Extract the 3 smallest elements of `vals` in $O(N)$ time without fully sorting the array.
43. Extract the 3 largest elements of `vals` using `np.partition()`.
44. Find the indices that partition `vals` using `np.argpartition()`.
45. Extract the indices of the top 5 largest values in `vals` using `np.argpartition()`.
46. Sort only the top 5 largest elements extracted via `argpartition` to display them in descending order.
47. Partition a 2D matrix along its rows so that the median element of each row is placed at the middle index.
48. Extract the 2 smallest elements from each column of a 2D matrix using `np.partition(mat, 2, axis=0)`.
49. Find the median of an unsorted array in $O(N)$ expected time using `np.partition()` and index indexing.
50. What is the time complexity difference between `np.sort()` ($O(N \log N)$) and `np.partition()` ($O(N)$)?


## Counting, Binning & Frequency Histograms

Use:
```python
scores = np.array([1, 2, 2, 3, 3, 3, 4, 4, 4, 4, 0, 1, 5, 5])
```

51. Count the occurrences of each non-negative integer in `scores` using `np.bincount()`.
52. Specify `minlength=8` in `np.bincount()` to ensure counts up to integer 7 are included.
53. Compute weighted bin counts where each occurrence is weighted by a value in `weights = np.arange(len(scores))`.
54. Find the most frequent element (mode) of `scores` using `np.bincount()` and `np.argmax()`.
55. Compute a 1D frequency histogram with 5 bins over continuous data using `np.histogram()`.
56. Extract both bin counts and bin edge boundaries from `np.histogram()`.
57. Compute a normalized probability density histogram using `density=True` in `np.histogram()`.
58. Assign each continuous data point to a discrete bin index using `np.digitize()`.
59. Use `np.digitize()` with `right=True` versus `right=False` to observe boundary inclusiveness.
60. Compute a 2D joint histogram for coordinate pairs $(X, Y)$ using `np.histogram2d()`.
61. Compute an $N$-dimensional histogram for multivariate data using `np.histogramdd()`.
62. Group values in an array by category labels and compute the sum for each category using `np.bincount()`.
63. Group values by category labels and compute the mean for each category using `np.bincount(labels, weights=values) / np.bincount(labels)`.
64. Find all bins that have zero occurrences from histogram outputs.
65. Count the number of elements falling within a closed range $[a, b]$ using `np.count_nonzero()`.


## Advanced: Searchsorted, Intervals & Matching

66. Use `np.searchsorted()` on a sorted array `s = np.array([10, 20, 30, 40, 50])` to find insertion positions for `[15, 25, 35]`.
67. Use `np.searchsorted()` to test whether elements of an unsorted query array exist in a sorted reference array.
68. Find the nearest neighbor value in a sorted 1D array for an arbitrary query point using `np.searchsorted()`.
69. Piecewise step function evaluation: evaluate a step function defined by thresholds and values using `np.searchsorted()`.
70. Find the index of the first value greater than a threshold in a sorted array.
71. Find the index of the last value smaller than a threshold in a sorted array.
72. Search for multiple values simultaneously in a sorted 1D array using vectorized `np.searchsorted()`.
73. Map continuous values into quantile categories (0, 1, 2, 3) using quartile thresholds and `np.searchsorted()`.
74. Match rows of matrix $A$ to identical rows in matrix $B$ using sorting and search tools.
75. Implement an efficient set difference $A \setminus B$ for large arrays using sorting and `np.isin()`.
76. Find common elements (set intersection) between two 1D arrays using `np.intersect1d()`.
77. Find all unique elements across two arrays (set union) using `np.union1d()`.
78. Find elements that are in either $A$ or $B$ but not both (symmetric difference) using `np.setxor1d()`.
79. Find elements in $A$ that are not in $B$ using `np.setdiff1d()`.
80. Check whether array $A$ is a subset of array $B$ using `np.isin()` and `np.all()`.


## 3D & Tensor Sorting & Searching

Use:
```python
tensor = np.random.default_rng(42).integers(0, 100, size=(2, 3, 4))
```

81. Sort `tensor` along the last axis (`axis=-1`).
82. Sort `tensor` along axis 1 (across rows).
83. Sort `tensor` along axis 0 (across depth slices).
84. Find the indices of the maximum value along the last axis using `np.argmax(tensor, axis=-1)`.
85. Find the 3D coordinates `(depth, row, col)` of the maximum element in the entire tensor.
86. Partition `tensor` along axis 2 to find the 2 smallest values in each row of each slice.
87. Count how many elements in `tensor` exceed 50 across each 2D slice (`axis=(1, 2)`).
88. Sort each 2D matrix inside `tensor` independently by its first column.
89. Obtain argsort indices for each 1D tube along axis 0.
90. Extract the top-2 elements along axis 1 for each slice using `argpartition`.


## Challenge Questions: Sorting Algorithms & Fast Queries

91. **Top-K Nearest Neighbors (KNN)**: Given query point $q \in \mathbb{R}^D$ and dataset $X \in \mathbb{R}^{N \times D}$, find the indices of the $K$ closest points using Euclidean distance and `np.argpartition()`.
92. **Cumulative Frequency Distribution (ECDF)**: Compute the empirical cumulative distribution function $\hat{F}(x)$ of a sample array using `np.sort()` and `np.arange()`.
93. **Stable Sorting**: Demonstrate stable sorting by sorting a structured array of records with identical primary keys using `kind='stable'`.
94. **Radix / Quicksort / Mergesort Comparison**: Compare sorting performance between `kind='quicksort'`, `kind='mergesort'`, and `kind='heapsort'`.
95. **Rank Transform**: Compute the fractional or dense ranks of elements in a 1D array using `np.argsort()` twice.
96. **Invert Permutation**: Given a permutation vector $p$, compute the inverse permutation vector $p^{-1}$ such that $p[p^{-1}] = \text{arange}(N)$.
97. **Fast Running Median**: Efficiently find the median in sliding windows using partitioning or bisect search.
98. **Finding Longest Consecutive Run**: Find the length of the longest consecutive sequence of identical numbers in a 1D array using `np.diff()` and `np.where()`.
99. **Two-Sum Problem**: Find two indices in an unsorted array whose values sum to target $T$ using sorting and two-pointer logic or hash matching.
100. **Matrix Profile Minima**: Given a pairwise distance matrix between time-series snippets, find the 1-NN index for each snippet using `np.argmin()`.

---

Try solving as many questions as possible using NumPy's sorting and searching utilities (`sort`, `argsort`, `partition`, `argpartition`, `searchsorted`, `unique`, `bincount`) without using Python `for` loops.
