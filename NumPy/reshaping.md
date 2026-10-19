# Array Manipulation & Reshaping Question Bank Compiled by AutoMind Team

## Beginner: Reshaping, Flattening & Raveling

Use this setup for Questions 1–20:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import numpy as np                                         %
%                                                            %
% arr1d = np.arange(1, 25)                                   %
% arr2d = np.arange(1, 13).reshape(3, 4)                     %
%                                                            %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Reshape `arr1d` from shape `(24,)` into a 2D array of shape `(4, 6)` using `.reshape()`.
2. Reshape `arr1d` into a 2D array of shape `(6, 4)`.
3. Reshape `arr1d` into a 3D array of shape `(2, 3, 4)`.
4. Reshape `arr1d` into a 2D array with 3 rows, allowing NumPy to infer the number of columns using `-1`.
5. Reshape `arr1d` into a 2D array with 8 columns using `-1` for rows.
6. Flatten `arr2d` into a 1D array using `.flatten()`.
7. Flatten `arr2d` into a 1D array using `.ravel()`.
8. Explain the critical difference between `.flatten()` and `.ravel()` regarding memory views vs copies.
9. Modify an element of a flattened array created by `.ravel()` and check if the original array changes.
10. Modify an element of an array created by `.flatten()` and verify that the original array remains unchanged.
11. Flatten `arr2d` in column-major (Fortran) order using `.ravel(order='F')`.
12. Reshape `arr1d` into `(4, 6)` using Fortran memory order (`order='F'`).
13. Check the number of dimensions of `arr1d` and `arr2d` using `.ndim`.
14. Check the total number of elements in `arr2d` using `.size`.
15. Check the byte size of each element in `arr2d` using `.itemsize`.
16. Resize an array `a = np.array([1, 2, 3])` to length 6 using `np.resize()` (which cycles elements).
17. Explain the difference between `np.resize()` and `ndarray.resize()`.
18. Convert a 1D array `x` of length 5 into a row vector of shape `(1, 5)`.
19. Convert a 1D array `x` of length 5 into a column vector of shape `(5, 1)`.
20. Check whether an array's memory is contiguous using `arr2d.flags['C_CONTIGUOUS']`.


## Intermediate: Dimension Expansion, Squeezing & Transposition

Use:
```python
arr = np.arange(1, 13).reshape(3, 4)
tensor = np.arange(24).reshape(2, 1, 3, 1, 4)
```

21. Add a new leading axis to `arr` to convert shape `(3, 4)` to `(1, 3, 4)` using `np.newaxis`.
22. Add a new trailing axis to `arr` to convert shape `(3, 4)` to `(3, 4, 1)` using `None`.
23. Insert a new axis at position 1 in `arr` to obtain shape `(3, 1, 4)` using `np.expand_dims()`.
24. Insert two new axes at positions 0 and 2 simultaneously using `np.expand_dims(arr, axis=(0, 2))`.
25. Remove all single-dimensional axes from `tensor` using `np.squeeze()` to get shape `(2, 3, 4)`.
26. Squeeze only the axis at index 1 from `tensor` using `np.squeeze(tensor, axis=1)`.
27. What happens if you try to squeeze an axis whose length is greater than 1?
28. Transpose `arr` using the `.T` attribute. What is the resulting shape?
29. Transpose `arr` using `np.transpose()`.
30. Reverse the axes of a 3D array of shape `(2, 3, 4)` using `np.transpose()`.
31. Permute the axes of a 3D array of shape `(2, 3, 4)` to shape `(3, 4, 2)` using `np.transpose(arr, (1, 2, 0))`.
32. Swap the first and last axes of a 3D array using `np.swapaxes()`.
33. Move axis 2 to position 0 in a 3D array using `np.moveaxis()`.
34. Move the batch axis (position 0) to the last position in a 4D tensor using `np.moveaxis(tensor, 0, -1)`.
35. Swap axis 1 and axis 3 of a 4D tensor of shape `(10, 3, 32, 32)` using `np.swapaxes()`.
36. Roll an array `x = np.arange(10)` forward by 3 positions using `np.roll()`.
37. Roll an array `x = np.arange(10)` backward by 2 positions using `np.roll()`.
38. Roll a 2D matrix by 1 position along rows (axis 0) using `np.roll()`.
39. Roll a 2D matrix by 2 positions along columns (axis 1) using `np.roll()`.
40. Roll a 2D matrix along both axes simultaneously using `np.roll(matrix, shift=(1, 2), axis=(0, 1))`.


## 2D Matrix Manipulations: Flipping, Rotating & Repeating

Use:
```python
mat = np.array([
    [ 1,  2,  3,  4],
    [ 5,  6,  7,  8],
    [ 9, 10, 11, 12]
])
```

41. Flip `mat` vertically (upside down) using `np.flipud()`.
42. Flip `mat` horizontally (left to right) using `np.fliplr()`.
43. Flip `mat` along both axes simultaneously using `np.flip()`.
44. Flip only axis 1 of `mat` using `np.flip(mat, axis=1)`.
45. Rotate `mat` by 90 degrees counter-clockwise using `np.rot90()`.
46. Rotate `mat` by 180 degrees using `np.rot90(mat, k=2)`.
47. Rotate `mat` by 270 degrees counter-clockwise (or 90 degrees clockwise) using `np.rot90(mat, k=3)`.
48. Rotate `mat` clockwise by 90 degrees using `np.rot90(mat, k=-1)`.
49. Repeat each element of a 1D array `a = np.array([1, 2, 3])` 4 times using `np.repeat()`.
50. Repeat rows of `mat` 2 times along axis 0 using `np.repeat()`.
51. Repeat columns of `mat` 3 times along axis 1 using `np.repeat()`.
52. Repeat each row of `mat` with a different count: row 0 once, row 1 twice, row 2 three times.
53. Tile `mat` 2 times vertically and 3 times horizontally using `np.tile()`.
54. Tile a 1D vector `v = np.array([1, 2])` to shape `(3, 4)` using `np.tile()`.
55. Trim zeros from the front and back of a 1D array `z = np.array([0, 0, 1, 2, 0, 3, 0])` using `np.trim_zeros()`.
56. Trim only leading zeros from `z` using `np.trim_zeros(z, trim='f')`.
57. Trim only trailing zeros from `z` using `np.trim_zeros(z, trim='b')`.
58. Pad a 1D array `a = np.array([1, 2, 3])` with 2 zeros on both sides using `np.pad()`.
59. Pad a 2D matrix with a 1-pixel border of constant value -1 using `np.pad()`.
60. Pad a 2D matrix using edge reflection (`mode='reflect'`).


## Advanced: Strides, Views & Shape Transformations

61. Inspect the strides of a 2D array of shape `(3, 4)` and explain what the tuple represents.
62. Create an as-strided sliding window view of length 3 over a 1D array using `np.lib.stride_tricks.sliding_window_view()`.
63. Extract all 2×2 non-overlapping patches from a 4×4 matrix using `sliding_window_view()` with step slicing.
64. Extract all 3×3 sliding windows from an image matrix of shape `(10, 10)` using `sliding_window_view()`.
65. Make an array C-contiguous after non-contiguous slicing using `np.ascontiguousarray()`.
66. Make an array Fortran-contiguous using `np.asfortranarray()`.
67. Broadcast a 1D array `x = np.array([1, 2, 3])` to shape `(4, 3)` using `np.broadcast_to()`.
68. Check whether `np.broadcast_to()` shares memory with the original input using `np.shares_memory()`.
69. Inspect the `.strides` of an array generated by `np.broadcast_to()` and identify which axis has stride 0.
70. Flatten a multi-dimensional array into a 1D view using `arr.reshape(-1)`.
71. Transpose a 2D matrix without using `.T` or `transpose()` (using `arr.swapaxes(0, 1)`).
72. Convert a matrix of shape `(M, N)` to shape `(N, M)` such that elements are read column-by-column into rows.
73. Reshape a 1D array of 12 elements into `(2, 2, 3)` and explain how elements are distributed across dimensions.
74. Given an array of shape `(4, 6)`, reshape it to `(2, 2, 2, 3)` without altering the total element count.
75. Flatten only the spatial dimensions of an image batch of shape `(N, C, H, W)` into `(N, C, H * W)`.
76. Convert a batch of image tensors from NCHW format `(32, 3, 64, 64)` to NHWC format `(32, 64, 64, 3)`.
77. Convert an array from NHWC format `(16, 28, 28, 1)` to NCHW format `(16, 1, 28, 28)`.
78. Combine batch and channel dimensions of `(B, C, H, W)` into `(B * C, H, W)` using `reshape()`.
79. Reverse the elements along axis 1 of a 2D array using slice syntax `[:, ::-1]`.
80. Reverse the elements along both axes of a 2D array using `mat[::-1, ::-1]`.


## 3D & 4D Tensor Reshaping

Use:
```python
tensor = np.arange(60).reshape(3, 4, 5)
```

81. Permute the dimensions of `tensor` from `(3, 4, 5)` to `(5, 3, 4)`.
82. Swap the first and second dimensions of `tensor` using `np.swapaxes(tensor, 0, 1)`.
83. Flatten each 2D matrix of `tensor` into a vector, producing shape `(3, 20)`.
84. Expand `tensor` by adding a channel dimension at index 1 to produce shape `(3, 1, 4, 5)`.
85. Squeeze all unit dimensions out of an array of shape `(1, 10, 1, 20, 1)`.
86. Reshape a 3D tensor of shape `(2, 3, 4)` into a 1D array and then reconstruct the original tensor.
87. Split a 4D tensor `(10, 8, 16, 16)` into two tensors of shape `(5, 8, 16, 16)` along the batch axis.
88. Tile a 3D tensor of shape `(2, 3, 4)` twice along axis 0 to produce shape `(4, 3, 4)`.
89. Repeat the middle axis of `(2, 3, 4)` three times to produce shape `(2, 9, 4)`.
90. Roll a 3D array along axis 2 by 1 position.


## Challenge Questions: Advanced Reshaping & Tensor Rearrangements

91. **Sub-Pixel Convolution (Pixel Shuffle)**: Reshape a tensor of shape `(1, 4, 8, 8)` to shape `(1, 1, 16, 16)` using `reshape()` and `transpose()` to simulate a 2× super-resolution pixel shuffle.
92. **Patch Extraction / Im2Col**: Given an image matrix of shape `(16, 16)`, reshape and transpose it into a collection of non-overlapping 4×4 patches of shape `(16, 4, 4)`.
93. **Block Matrix Unraveling**: Given a 4×4 matrix, reshape it into a 2×2 grid of 2×2 blocks of shape `(2, 2, 2, 2)`.
94. **Flattening Upper Triangle**: Extract and flatten only the upper triangular elements of a square matrix into a 1D vector without loops.
95. **Interleaving Two Arrays**: Given two 1D arrays `a = [1, 3, 5]` and `b = [2, 4, 6]`, interleave them into `[1, 2, 3, 4, 5, 6]` using `np.stack()` and `ravel()`.
96. **Vectorized Outer Reshape**: Given vectors `u` of length $M$ and `v` of length $N$, construct an $(M, N)$ coordinate grid using dimension expansion and broadcasting.
97. **Flattening Ragged Arrays**: Convert a list of variable-length 1D arrays into a 2D padded matrix with sentinel values using array allocation and masking.
98. **Diagonal Block Assembly**: Assemble four 2×2 blocks into a 4×4 block matrix using nested list reshaping.
99. **Multi-Axis Rolling**: Implement a periodic 2D boundary shift for cellular automata simulation using `np.roll()` across both axes.
100. **Strided Diagonal Extraction**: Extract the main diagonal of an $N \times N$ matrix by manipulating strides with `np.lib.stride_tricks.as_strided()`.

---

Try solving as many questions as possible using NumPy's reshaping and manipulation tools (`reshape`, `ravel`, `transpose`, `swapaxes`, `expand_dims`, `squeeze`, `pad`, `roll`) without using Python `for` loops.
