# Array Creation & Generators Question Bank Compiled by AutoMind Team

## Beginner: Basic Creation Functions & Ranges

Use this setup for Questions 1–20:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import numpy as np                                         %
%                                                            %
% # Basic initializations: zeros, ones, full, arange, linspace%
%                                                            %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Create a 1D array of 10 zeros with `float64` data type using `np.zeros()`.
2. Create a 1D array of 5 ones with integer type (`int32`) using `np.ones()`.
3. Create a 2D array of shape `(3, 4)` filled entirely with zeros.
4. Create a 3D array of shape `(2, 3, 4)` filled with ones.
5. Create a 1D array of length 7 filled entirely with the constant value 42 using `np.full()`.
6. Create a 2D array of shape `(3, 3)` filled with the string `'empty'`.
7. Create an uninitialized array of shape `(5, 5)` using `np.empty()` and explain what values it contains.
8. Create an array of integers from 0 to 9 (inclusive) using `np.arange()`.
9. Create an array of even numbers from 10 to 30 (inclusive) with a step of 2 using `np.arange()`.
10. Create an array of numbers from 10 down to 1 with a step of -1 using `np.arange()`.
11. Create an array of 50 equally spaced numbers between 0.0 and 1.0 (inclusive) using `np.linspace()`.
12. Create an array of 5 equally spaced values between 0 and 100 with `endpoint=False`.
13. Create an array using `np.linspace()` and return the step size used between elements using `retstep=True`.
14. Create an array of 10 numbers logarithmically spaced between $10^1$ and $10^4$ using `np.logspace()`.
15. Create an array of 8 geometrically spaced numbers between 2 and 256 with base 2 using `np.geomspace()`.
16. Create a 1D array from a Python list `[3, 14, 15, 92, 65]` using `np.array()`.
17. Create a 2D array from a nested Python list `[[1, 2], [3, 4], [5, 6]]`.
18. Create an array of boolean values `[True, False, True, True]` using `np.array()`.
19. Create an array with complex numbers `1 + 2j`, `3 - 4j` using `np.array()` with `dtype=complex128`.
20. Convert an existing tuple `(10, 20, 30)` into a NumPy array using `np.asarray()`.


## Intermediate: Like-Constructors, Diagonals & Identity Matrices

Use:
```python
ref_arr = np.array([[1, 2, 3], [4, 5, 6]])
```

21. Create an array of zeros with the exact same shape and data type as `ref_arr` using `np.zeros_like()`.
22. Create an array of ones with the same shape and type as `ref_arr` using `np.ones_like()`.
23. Create an array of shape and type like `ref_arr` filled with value -1 using `np.full_like()`.
24. Create an uninitialized array with the same properties as `ref_arr` using `np.empty_like()`.
25. Create a 4×4 identity matrix using `np.eye()`.
26. Create a 5×5 identity matrix using `np.identity()`.
27. Using `np.eye()`, create a 4×5 matrix with the diagonal of 1s shifted by $k = 1$ (above the main diagonal).
28. Using `np.eye()`, create a 5×4 matrix with the diagonal of 1s shifted by $k = -1$ (below the main diagonal).
29. Extract the main diagonal from a 2D matrix `M = np.arange(16).reshape(4, 4)` using `np.diag()`.
30. Given a 1D vector `v = np.array([2, 4, 6, 8])`, construct a 2D square matrix with `v` on the main diagonal using `np.diag()`.
31. Given `v = np.array([1, 3, 5])`, construct a 4×4 matrix with `v` placed on the super-diagonal ($k = 1$).
32. Given `v = np.array([7, 8, 9])`, construct a 4×4 matrix with `v` placed on the sub-diagonal ($k = -1$).
33. Create a 4×4 scalar matrix where all diagonal elements are 7 and off-diagonal elements are 0.
34. Create a 3×3 lower triangular matrix of ones using `np.tri()`.
35. Create a 4×5 lower triangular matrix using `np.tri()` with diagonal offset $k = -1$.
36. Given a square matrix `A`, zero-out all elements above the main diagonal using `np.tril()`.
37. Given a square matrix `A`, zero-out all elements below the main diagonal using `np.triu()`.
38. Extract the strictly upper triangular part of matrix `A` (excluding the main diagonal) using `k=1` in `np.triu()`.
39. Given a 1D array `x = np.array([1, 2, 3, 4])`, generate a Vandermonde matrix using `np.vander()`.
40. Generate a Vandermonde matrix with only 3 columns using `np.vander(x, N=3)`.


## 2D Coordinate Grids & Index Arrays

Use:
```python
x = np.linspace(-5, 5, 5)
y = np.linspace(-3, 3, 4)
```

41. Create 2D coordinate matrices `X` and `Y` from `x` and `y` using `np.meshgrid()`.
42. Create coordinate matrices using `np.meshgrid()` with Cartesian indexing (`indexing='xy'`).
43. Create coordinate matrices using `np.meshgrid()` with matrix indexing (`indexing='ij'`).
44. Create sparse open coordinate arrays using `np.ogrid` over ranges `0:5` and `0:5`.
45. Create dense coordinate grids using `np.mgrid` over slices `0:4, 0:5`.
46. Create float coordinate grids between 0 and 1 with 5 steps using `np.mgrid[0:1:5j, 0:1:5j]`.
47. Evaluate the 2D Gaussian function $f(x, y) = \exp(-(x^2 + y^2))$ over a grid generated by `np.meshgrid()`.
48. Generate an array of multi-dimensional indices for shape `(3, 4)` using `np.indices()`.
49. Extract open mesh arrays for cross-indexing using `np.ix_()` for row indices `[0, 2]` and column indices `[1, 3]`.
50. Generate a grid of coordinate pairs of shape `(5, 5, 2)` combining `X` and `Y` using `np.stack()`.
51. Create a 5×5 multiplication grid using `np.fromfunction()` with function `lambda i, j: (i + 1) * (j + 1)`.
52. Create an 8×8 checkerboard pattern of 0s and 1s using `np.indices()`.
53. Create a circular mask of radius $R = 4$ on a 10×10 grid using `np.ogrid`.
54. Construct a distance grid from the center of a 9×9 matrix using coordinate indexing.
55. Create a 3D coordinate grid using `np.meshgrid()` with three 1D arrays of length 3.
56. Create a 1D array containing all combinations of two 1D coordinate vectors using `np.meshgrid()` and `ravel()`.
57. Generate coordinate indices for the lower triangular elements of a 4×4 matrix using `np.tril_indices(4)`.
58. Generate coordinate indices for the upper triangular elements of a 5×5 matrix using `np.triu_indices(5)`.
59. Generate diagonal coordinate indices for an $N \times N$ matrix using `np.diag_indices(N)`.
60. Create a 5×5 symmetric distance matrix using coordinate differences from `np.indices()`.


## Advanced: From Buffers, Iterables & Custom Data

61. Create a NumPy array from a Python generator or iterator using `np.fromiter()`.
62. Create an array of 8-bit integers from a raw binary byte string `b'\x01\x02\x03\x04'` using `np.frombuffer()`.
63. Create an array of float numbers from a text string containing comma-separated values using `np.fromstring()`.
64. Create an array from an open file-like object using `np.fromfile()`.
65. Convert a memoryview object into a NumPy array without copying data.
66. Create a 1D NumPy array by repeating an initial pattern `[1, 2, 3]` five times using `np.tile()`.
67. Create a 1D array by repeating each element of `[1, 2, 3]` three times consecutively using `np.repeat()`.
68. Create a 2D array by tiling a 2×2 identity matrix 3 times vertically and 2 times horizontally.
69. Create an empty array and fill it with values using a function of its coordinates with `np.fromfunction()`.
70. Create a structured array with fields `('name', 'U10')` and `('age', 'i4')` initialized with zeros.
71. Initialize a constant array of shape `(3, 3)` using `np.broadcast_to()` from a single scalar.
72. Create a NumPy array from a nested dictionary or JSON-like object by mapping keys to structured types.
73. Create a custom diagonal block matrix from three 2×2 matrices using `scipy.linalg.block_diag` or NumPy concatenation.
74. Create a 1D array using `np.arange()` with non-integer float steps and explain the potential precision pitfalls.
75. Create a stepped range array using `np.linspace()` to avoid floating point drift associated with `np.arange()`.
76. Create a 10-element array of random seed integers using `np.random.SeedSequence().generate_state()`.
77. Create an array containing datetime objects spanning every day in October 2026 using `np.arange('2026-10-01', '2026-11-01', dtype='datetime64[D]')`.
78. Create an array of hourly timestamps for 24 hours using `np.arange(dtype='datetime64[h]')`.
79. Create an array of timedelta values representing 1 to 10 minutes using `np.arange(1, 11, dtype='timedelta64[m]')`.
80. Create a 2D array representing a rotation matrix for an angle $\theta = \pi / 4$.


## 3D & Multi-Dimensional Array Creation

Use:
```python
dim = (2, 3, 4)
```

81. Initialize a 3D tensor of shape `(2, 3, 4)` with consecutive integers starting from 1.
82. Create a 4D tensor of shape `(10, 3, 32, 32)` representing a batch of 10 RGB images of size 32×32 filled with zeros.
83. Initialize a 3D tensor of shape `(4, 4, 4)` with ones on the main 3D diagonal ($A_{iii} = 1$) and zeros elsewhere.
84. Create a 3D coordinate mesh using `np.mgrid[0:2, 0:3, 0:4]`.
85. Initialize a 3D array filled with `np.nan` values of shape `(3, 4, 5)` with `dtype=float64`.
86. Create a 3D tensor of zeros and set the center element to 1 (3D Dirac delta impulse).
87. Create a 3D array of shape `(2, 2, 2)` filled with alternating `True` and `False` booleans.
88. Create an uninitialized 3D buffer of shape `(100, 100, 100)` with `np.empty()` for memory benchmarking.
89. Create a 3D tensor where each slice $k$ along axis 0 is a $k \times I$ identity matrix.
90. Construct a 3D array of shape `(3, 3, 3)` using `np.fromfunction()` where $A_{ijk} = i + j + k$.


## Challenge Questions: Special Matrices & Numerical Builders

91. **Companion Matrix**: Given polynomial coefficients $p = [1, -5, 6]$, construct its companion matrix using `np.diag()` and `np.zeros()`.
92. **Toeplitz Matrix**: Construct a symmetric Toeplitz matrix where the first row is `[1, 0.5, 0.25, 0.125]` using `np.abs(np.subtract.outer())`.
93. **Circulant Matrix**: Construct a 4×4 circulant matrix from vector `c = [1, 2, 3, 4]` without using external libraries.
94. **Hilbert Matrix**: Construct an $N \times N$ Hilbert matrix where $H_{ij} = \frac{1}{i + j - 1}$ using `np.fromfunction()` or broadcasting.
95. **Hankel Matrix**: Construct an $N \times N$ Hankel matrix where elements along the anti-diagonals are constant using index broadcasting.
96. **Pascal Matrix**: Generate an $N \times N$ symmetric Pascal matrix using binomial coefficients computed via NumPy vectorization.
97. **Fourier Matrix (DFT Basis)**: Generate an $N \times N$ Discrete Fourier Transform matrix $W_{jk} = \exp(-2\pi i j k / N) / \sqrt{N}$ using `np.fromfunction()`.
98. **Lehmer Matrix**: Construct a 5×5 Lehmer matrix where $A_{ij} = \min(i, j) / \max(i, j)$ using 1-based indexing.
99. **Red-Black Grid Builder**: Generate a 2D red-black (checkerboard) grid mask for numerical PDE solver grid partitioning.
100. **Memory-Mapped Array Creation**: Create a persistent disk-backed array of shape `(1000, 1000)` using `np.memmap()` in write mode.

---

Try solving as many questions as possible using NumPy's built-in creation utilities (`zeros`, `ones`, `arange`, `linspace`, `meshgrid`, `diag`, `indices`) without using Python `for` loops.
