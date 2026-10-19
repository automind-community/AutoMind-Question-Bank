# Data Types, Memory Layout & Views vs Copies Question Bank Compiled by AutoMind Team

## Beginner: Dtypes, Inspection & Type Casting

Use this setup for Questions 1–20:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import numpy as np                                         %
%                                                            %
% a = np.array([1, 2, 3, 4, 5])                              %
% b = np.array([1.5, 2.7, 3.2])                              %
%                                                            %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Check the data type of array `a` using `.dtype`.
2. Check the data type of array `b`.
3. Check the item size (number of bytes per element) of `a` using `.itemsize`.
4. Check the total memory bytes consumed by all elements of `a` using `.nbytes`.
5. Cast array `a` from `int64` to `float64` using `.astype(np.float64)`.
6. Cast array `b` from `float64` to `int32` and observe truncation.
7. Cast array `a` to boolean type (`bool`).
8. Create an array of 8-bit unsigned integers (`uint8`) with values `[0, 128, 255]`.
9. What happens when you store 256 in a `uint8` array (integer overflow)?
10. Check the minimum and maximum representable values for `int16` using `np.iinfo(np.int16)`.
11. Check machine limits, precision, and epsilon for `float32` using `np.finfo(np.float32)`.
12. Compare memory consumption between an array of 1,000,000 elements in `float64` vs `float32`.
13. Create an array with complex numbers using `dtype=np.complex128`.
14. Extract the real part of a complex array using `.real`.
15. Extract the imaginary part of a complex array using `.imag`.
16. Create a string array with fixed-length Unicode strings `dtype='<U10'`.
17. What happens if you assign a string longer than 10 characters to a `U10` string array?
18. Create an array of byte strings using `dtype='|S5'`.
19. Convert an array of numeric strings `np.array(['1.2', '3.4', '5.6'])` to float numbers using `.astype(float)`.
20. Check whether two data types are equal using `np.dtype(np.int32) == np.dtype('i4')`.


## Intermediate: Views vs Copies & Memory Sharing

Use:
```python
orig = np.arange(10)
```

21. Create a slice `sub = orig[2:7]`. Does `sub` create a view or a copy?
22. Modify `sub[0] = 999` and check if `orig` changes.
23. Check if `sub.base` points to `orig` to confirm it is a view.
24. Create an explicit deep copy of `orig` using `.copy()`.
25. Modify the copy and verify that `orig` is not altered.
26. Check the `.base` attribute of an explicit copy. What does it return?
27. Test whether two arrays share the same memory buffer using `np.shares_memory(orig, sub)`.
28. Test whether two arrays share memory using `np.may_share_memory()`.
29. Does fancy indexing `orig[[1, 3, 5]]` create a view or a copy?
30. Modify an array created via fancy indexing and verify that `orig` remains unchanged.
31. Does boolean masking `orig[orig > 5]` produce a view or a copy?
32. Does transposing a 2D matrix `mat.T` create a view or a copy?
33. Does reshaping an array with `reshape()` always create a view? When might it create a copy?
34. Check if `mat.ravel()` shares memory with `mat`.
35. Check if `mat.flatten()` shares memory with `mat`.
36. Check whether `np.squeeze()` produces a view.
37. Check whether `np.expand_dims()` produces a view.
38. Check whether `np.broadcast_to()` produces a view without copying data.
39. Demonstrate how in-place arithmetic `orig += 1` preserves the memory view while `orig = orig + 1` rebinds to a new array.
40. Use `.view()` to view `float64` array bytes as `int64` without data conversion (bitcasting).


## Memory Layout: Strides & C vs Fortran Contiguity

Use:
```python
mat = np.arange(12, dtype=np.int32).reshape(3, 4)
```

41. Inspect the memory strides of `mat` using `.strides`. Explain the two values `(row_stride, col_stride)`.
42. Check if `mat` is C-contiguous using `mat.flags['C_CONTIGUOUS']`.
43. Check if `mat` is Fortran-contiguous using `mat.flags['F_CONTIGUOUS']`.
44. Create a Fortran-contiguous copy of `mat` using `np.asfortranarray()`.
45. Check `.strides` of the Fortran-contiguous array and compare with C-contiguous strides.
46. Transpose `mat` (`mat_T = mat.T`). Is `mat_T` C-contiguous or Fortran-contiguous?
47. What are the `.strides` of `mat.T` compared to `mat`?
48. Convert a non-contiguous transposed array back to a C-contiguous array using `np.ascontiguousarray()`.
49. Slice every second column of `mat` (`mat[:, ::2]`). Is the slice contiguous?
50. What happens to the column stride when slicing with a step of 2?
51. Reverse rows using `mat[::-1, :]` and inspect how strides handle negative stepping.
52. Check whether an array is writeable using `mat.flags['WRITEABLE']`.
53. Make an array read-only by setting `mat.flags.writeable = False`.
54. Try modifying a read-only array and observe the `ValueError`.
55. Check array memory alignment using `mat.flags['ALIGNED']`.
56. Explain why iterating along the contiguous dimension is faster for cache locality.
57. Measure the time difference between summing a large C-contiguous matrix row-wise vs column-wise.
58. Flatten an array in Fortran order using `mat.ravel(order='F')` and check its contiguity.
59. Inspect `.flags` to see all memory and writeability properties of an array.
60. Create a 0-stride axis using `np.broadcast_to()` and verify that the stride along the broadcasted axis is 0.


## Advanced: Byte Ordering, Endianness & Low-Level Buffers

61. Check the byte order of an array's dtype using `arr.dtype.byteorder`.
62. Create an array with little-endian byte ordering using `dtype='<i4'`.
63. Create an array with big-endian byte ordering using `dtype='>i4'`.
64. Convert an array's byte order using `.byteswap()`.
65. Convert an array to the system's native byte order using `.newbyteorder('=')`.
66. View an array of four 8-bit integers (`uint8`) as a single 32-bit integer (`uint32`) using `.view()`.
67. View an array of 32-bit integers as four 8-bit integers and observe the byte breakdown.
68. Access the raw byte buffer of an array using `arr.tobytes()`.
69. Reconstruct a NumPy array from a raw byte buffer using `np.frombuffer()`.
70. Inspect the memory pointer address of an array's data buffer using `arr.__array_interface__['data'][0]`.
71. Verify that a view has the same base data pointer as the original array.
72. Check the memory layout and shape representation via `arr.__array_interface__`.
73. Determine whether an array owns its memory buffer using `arr.flags['OWNDATA']`.
74. Verify that `orig.flags['OWNDATA'] == True` while `view.flags['OWNDATA'] == False`.
75. Create an array from an external Python `bytearray` object without copying memory.
76. Cast an array with `copy=False` in `astype()` and observe behavior when the type matches vs changes.
77. Explain type promotion rules when adding `int32` and `float32` (resulting in `float64`).
78. Determine the resulting common type of two arrays using `np.result_type(a, b)`.
79. Check if a cast is safe without loss of precision using `np.can_cast(np.int32, np.int64)`.
80. Check whether `np.can_cast(np.float64, np.int32)` is considered safe.


## Multi-Dimensional Strides & Tensor Layouts

Use:
```python
tensor = np.arange(24).reshape(2, 3, 4)
```

81. Inspect the 3D strides of `tensor` of shape `(2, 3, 4)` with 8-byte integers.
82. Swap axis 0 and axis 2 of `tensor` and inspect how the strides tuple is permuted.
83. Squeeze a 4D array of shape `(2, 1, 3, 4)` and observe how strides change.
84. Check if a transposed 3D tensor owns its data.
85. Make a transposed 3D tensor C-contiguous using `np.ascontiguousarray()`.
86. Slice a 3D block `tensor[:, 1:3, ::2]` and check its contiguity flags.
87. Flatten a 3D tensor into a 1D view using `.reshape(-1)`.
88. Compute the byte offset of element `tensor[1, 2, 3]` using its indices and strides.
89. Compare the memory usage of a float16 tensor vs float64 tensor for a deep learning model layer.
90. Check if `np.moveaxis()` creates a view or a copy.


## Challenge Questions: Stride Tricks & Zero-Copy Algorithms

91. **Manual Diagonal View via Strides**: Given an $N \times N$ matrix, extract the main diagonal as a 1D view by manipulating strides with `np.lib.stride_tricks.as_strided()`.
92. **Zero-Copy Sliding Window**: Create a 2D sliding window matrix of shape `(N - W + 1, W)` from a 1D array of length $N$ using stride tricks.
93. **2D Convolution Patches (Im2Col)**: Generate a zero-copy strided view of all $3 \times 3$ patches from a 2D image matrix.
94. **Broadcasting Emulation via 0-Stride**: Manually construct an $(M, N)$ array broadcast from an $(M, 1)$ vector by setting the column stride to 0.
95. **In-Place Byte Swapping**: Perform an in-place endianness swap on a binary file buffer without loading copies into memory.
96. **Detecting Shared Overlapping Memory**: Detect if two array slices overlap in memory and would cause unsafe in-place reads/writes using `np.shares_memory()`.
97. **Subtyping ndarray**: Inspect `__array_finalize__` and subclass `np.ndarray` to create a custom array type with metadata.
98. **Structured Buffer Alignment**: Create a structured array with unaligned fields and observe memory padding bytes using `align=True`.
99. **Memoryview to NumPy Zero-Copy Interop**: Pass data from Python's standard `array.array` or `memoryview` into NumPy without copying.
100. **Strided Circular Buffer**: Simulate a circular rolling buffer of fixed capacity $K$ using strided views and modular arithmetic.

---

Try solving as many questions as possible by inspecting `.dtype`, `.itemsize`, `.nbytes`, `.strides`, `.flags`, `.base`, and using zero-copy view transformations without Python `for` loops.
