# Joining, Stacking & Splitting Question Bank Compiled by AutoMind Team

## Beginner: 1D Concatenation & Basic Stacking

Use this setup for Questions 1–20:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import numpy as np                                         %
%                                                            %
% a = np.array([1, 2, 3, 4])                                 %
% b = np.array([5, 6, 7, 8])                                 %
% c = np.array([9, 10, 11, 12])                              %
%                                                            %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Concatenate `a` and `b` end-to-end into a single 1D array of 8 elements using `np.concatenate()`.
2. Concatenate three 1D arrays `a`, `b`, and `c` into a single 1D array of 12 elements.
3. Stack `a` and `b` vertically to create a 2D array of shape `(2, 4)` using `np.vstack()`.
4. Stack `a` and `b` horizontally to create a 1D array of 8 elements using `np.hstack()`.
5. Stack `a` and `b` along a new first axis using `np.stack((a, b), axis=0)` to produce shape `(2, 4)`.
6. Stack `a` and `b` along a new second axis using `np.stack((a, b), axis=1)` to produce shape `(4, 2)`.
7. Stack `a` and `b` depth-wise to produce a 3D array of shape `(1, 4, 2)` using `np.dstack()`.
8. Stack `a` and `b` as columns of a 2D matrix using `np.column_stack()`.
9. Stack `a` and `b` as rows of a 2D matrix using `np.row_stack()`.
10. Combine `a` and `b` using the index expression helper `np.r_[a, b]`.
11. Combine `a` and `b` as 2D columns using `np.c_[a, b]`.
12. Append element 99 to the end of `a` using `np.append()`.
13. Append array `b` to the end of array `a` using `np.append()`.
14. Insert value 100 at index 2 of array `a` using `np.insert()`.
15. Insert values `[20, 30]` starting at index 1 of array `a`.
16. Delete the element at index 2 of array `a` using `np.delete()`.
17. Delete multiple elements at indices `[0, 3]` from array `a`.
18. Split array `a` into 2 equal halves of length 2 using `np.split()`.
19. Split a 1D array of length 10 into 5 equal parts using `np.split()`.
20. What error is raised when attempting to split an array of length 7 into 3 equal parts with `np.split()`?


## Intermediate: 2D Stacking & Axis Concatenation

Use:
```python
A = np.arange(1, 13).reshape(3, 4)
B = np.arange(13, 25).reshape(3, 4)
C = np.arange(25, 37).reshape(3, 4)
```

21. Concatenate `A` and `B` along rows (`axis=0`) to form a 2D array of shape `(6, 4)`.
22. Concatenate `A` and `B` along columns (`axis=1`) to form a 2D array of shape `(3, 8)`.
23. Stack `A` and `B` along a brand new axis 0 to form a 3D array of shape `(2, 3, 4)` using `np.stack()`.
24. Stack `A` and `B` along axis 1 to form a 3D array of shape `(3, 2, 4)`.
25. Stack `A` and `B` along the last axis to form a 3D array of shape `(3, 4, 2)`.
26. Vertically stack `A` and `B` using `np.vstack()`.
27. Horizontally stack `A` and `B` using `np.hstack()`.
28. Depth-stack `A` and `B` into shape `(3, 4, 2)` using `np.dstack()`.
29. Concatenate a 2D array `A` of shape `(3, 4)` with a 1D row vector of shape `(4,)`. How must the 1D array be reshaped first?
30. Concatenate `A` of shape `(3, 4)` with a 1D column vector of shape `(3,)` along axis 1.
31. Concatenate three matrices `A`, `B`, and `C` along axis 0 to create shape `(9, 4)`.
32. Concatenate three matrices `A`, `B`, and `C` along axis 1 to create shape `(3, 12)`.
33. Split `A` vertically into 3 separate 1D rows (or 1×4 matrices) using `np.vsplit()`.
34. Split `A` horizontally into 2 equal matrices of shape `(3, 2)` using `np.hsplit()`.
35. Split `A` along columns into 4 individual columns using `np.hsplit(A, 4)`.
36. Split an array of shape `(7, 4)` into 3 unequal sub-arrays along axis 0 using `np.array_split()`.
37. Split `A` at specific column indices 1 and 3 using `np.hsplit(A, [1, 3])`.
38. Split `A` at specific row index 2 using `np.vsplit(A, [2])`.
39. Combine four 2×2 matrices into a 4×4 block matrix using `np.block()`.
40. Construct a 2×2 block diagonal matrix where off-diagonal blocks are zeros using `np.block()`.


## 2D Matrix Assembly & Row/Column Insertion

Use:
```python
mat = np.arange(1, 10).reshape(3, 3)
new_row = np.array([10, 20, 30])
new_col = np.array([[100], [200], [300]])
```

41. Append `new_row` as the last row of `mat` using `np.vstack()`.
42. Prepend `new_row` as the first row of `mat`.
43. Append `new_col` as the last column of `mat` using `np.hstack()`.
44. Prepend `new_col` as the first column of `mat`.
45. Insert `new_row` between row 0 and row 1 of `mat` using `np.insert()`.
46. Insert a column of zeros at index 1 of `mat` using `np.insert()`.
47. Delete the entire second row (index 1) of `mat` using `np.delete(mat, 1, axis=0)`.
48. Delete the entire third column (index 2) of `mat` using `np.delete(mat, 2, axis=1)`.
49. Delete both the first and last rows of `mat` in a single call using `np.delete()`.
50. Delete multiple columns at indices `[0, 2]` using `np.delete()`.
51. Replace the diagonal of `mat` with values `[99, 99, 99]` using `np.fill_diagonal()`.
52. Concatenate `mat` with an identity matrix of the same size along columns to form an augmented matrix $[A \mid I]$.
53. Horizontally stack a matrix `mat` of shape `(3, 3)` with a column vector of ones of shape `(3, 1)` (adding an intercept term).
54. Given a feature matrix `X` of shape `(100, 10)` and label vector `y` of shape `(100,)`, combine them into a single dataset array of shape `(100, 11)`.
55. Given a 2D matrix, duplicate each row by stacking the matrix with itself row-wise.
56. Given a 2D matrix, duplicate each column by stacking the matrix with itself column-wise.
57. Unpack a 2D matrix of shape `(3, 4)` into 3 individual 1D row vectors using Python unpacking and `np.vsplit()`.
58. Unpack a 2D matrix into 4 column vectors using `np.hsplit()`.
59. Interleave the rows of two matrices `A` and `B` of identical shape `(3, 4)` so that rows alternate: $A_0, B_0, A_1, B_1, A_2, B_2$.
60. Interleave the columns of two matrices `A` and `B` of identical shape `(3, 4)` so that columns alternate.


## Advanced: Multi-Array Stacking & Dynamic Splitting

61. Stack a list of 10 arrays each of shape `(28, 28)` into a single tensor of shape `(10, 28, 28)` using `np.stack()`.
62. Concatenate a list of 5 arrays each of shape `(B_i, 64)` along axis 0 where each $B_i$ is variable.
63. Stack arrays along the last dimension using `np.stack(arrays, axis=-1)`.
64. Split a 1D array of 100 elements into 5 folds of 20 elements each for 5-fold cross validation.
65. Split a 2D array of shape `(100, 10)` into train (80 rows) and test (20 rows) splits using `np.split()`.
66. Split a dataset into train (70%), validation (15%), and test (15%) splits using integer index boundaries with `np.split()`.
67. Combine arrays along a new channel dimension at axis 1 using `np.stack(arrays, axis=1)`.
68. Combine three grayscale image matrices of shape `(H, W)` into a single RGB image of shape `(H, W, 3)` using `np.dstack()`.
69. Split an RGB image of shape `(H, W, 3)` into three separate color channels (R, G, B) using `np.dsplit()`.
70. Given an array of shape `(6, 6)`, split it into four 3×3 quadrants using `np.vsplit()` and `np.hsplit()`.
71. Reassemble four 3×3 quadrants back into the original 6×6 matrix using `np.block()`.
72. Stack two 1D arrays `x` and `y` to create a 2D array of coordinate pairs `[[x0, y0], [x1, y1], ...]`.
73. Concatenate arrays along axis 0 without copying data if memory layout permits.
74. Use `np.r_` with slice syntax `np.r_[0:10:2, 10:20:3]` to combine multiple range sequences.
75. Use `np.r_['r', [1, 2, 3], [4, 5, 6]]` to concatenate as a matrix.
76. Use `np.c_` to concatenate 1D arrays directly into a 2D column table.
77. Insert a row of `np.nan` values at the top of a 2D matrix.
78. Split a continuous signal array into overlapping chunks using sliding windows versus non-overlapping chunks using `np.split()`.
79. Concatenate empty arrays with non-empty arrays and describe how shapes and dtypes are preserved.
80. Safely append rows to an empty 2D array initialized with shape `(0, 5)`.


## 3D & 4D Tensor Stacking & Splitting

Use:
```python
T1 = np.ones((2, 3, 4))
T2 = np.zeros((2, 3, 4))
```

81. Concatenate `T1` and `T2` along the first dimension (depth/batch) to produce shape `(4, 3, 4)`.
82. Concatenate `T1` and `T2` along the second dimension (rows) to produce shape `(2, 6, 4)`.
83. Concatenate `T1` and `T2` along the third dimension (columns) to produce shape `(2, 3, 8)`.
84. Stack `T1` and `T2` along a new leading axis to produce a 4D tensor of shape `(2, 2, 3, 4)`.
85. Split a 3D tensor of shape `(4, 3, 4)` along axis 0 into 4 separate 2D matrices of shape `(3, 4)`.
86. Split a 3D tensor along axis 2 into 2 equal halves of shape `(2, 3, 2)`.
87. Split a 3D tensor along axis 2 into 4 separate slices using `np.dsplit()`.
88. Concatenate a batch of image tensors `(32, 3, 64, 64)` and `(16, 3, 64, 64)` along the batch dimension.
89. Split a mini-batch tensor of shape `(64, 10)` into 4 micro-batches of shape `(16, 10)` each.
90. Join two 3D tensors along axis -1 to double the feature dimension.


## Challenge Questions: Advanced Assembly & Pipeline Splitting

91. **K-Fold CV Generator**: Write a function that splits a dataset of $N$ rows into $K$ folds, returning training and validation arrays for each fold using `np.concatenate()`.
92. **Kronecker Product**: Compute the Kronecker product of two matrices $A \otimes B$ using `np.kron()`.
93. **Block Diagonal Construction**: Construct a block diagonal matrix from a list of variable-size square matrices using `scipy.linalg.block_diag` or NumPy padding and block concatenation.
94. **Matrix Augmentation**: Assemble the block system $egin{pmatrix} A & B \ C & D \end{pmatrix}$ from four sub-matrices of compatible dimensions using `np.block()`.
95. **Dynamic Batch Concatenation**: Given a stream of 1D sensor readings arriving at irregular lengths, accumulate and concatenate them into a single contiguous 1D buffer.
96. **Un-padding Array**: Given an array padded with zeros on all borders, detect the bounding box of non-zero elements and crop the array back to its original shape.
97. **Pairwise Tile and Concatenate**: Given two 1D vectors $x$ and $y$, construct a 2D array of all possible coordinate pairs without explicit Python loops.
98. **Time Series Rolling Split**: Split a time-series vector into training windows of size $W$ and forecast horizons of size $H$ using indexing and stacking.
99. **Channel-First to Channel-Last Assembly**: Given three 2D matrices representing R, G, and B color planes, assemble them into both NCHW `(1, 3, H, W)` and NHWC `(1, H, W, 3)` formats.
100. **Ragged Sequence Padding & Stacking**: Given a list of 1D arrays of differing lengths, pad each with zeros to the maximum length and stack them into a uniform 2D matrix.

---

Try solving as many questions as possible using NumPy's joining and splitting functions (`concatenate`, `stack`, `vstack`, `hstack`, `dstack`, `block`, `split`, `array_split`) without using Python `for` loops.
