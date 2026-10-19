# Vectorization & Universal Functions (ufuncs) Question Bank Compiled by AutoMind Team

## Beginner: Basic Universal Functions & Math Routines

Use this setup for Questions 1–20:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import numpy as np                                         %
%                                                            %
% x = np.array([0.0, 1.0, 2.0, 3.0, 4.0])                     %
% y = np.array([1.0, 2.0, 3.0, 4.0, 5.0])                     %
%                                                            %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Add arrays `x` and `y` using the universal function `np.add(x, y)`.
2. Subtract `y` from `x` using `np.subtract(x, y)`.
3. Multiply `x` and `y` element-wise using `np.multiply(x, y)`.
4. Divide `x` by `y` using `np.divide(x, y)`.
5. Compute the power $x^y$ element-wise using `np.power(x, y)`.
6. Compute the square root of each element in `y` using `np.sqrt()`.
7. Compute the exponential ($e^x$) using `np.exp()`.
8. Compute the base-e natural logarithm of `y` using `np.log()`.
9. Compute the base-10 logarithm of `y` using `np.log10()`.
10. Compute the base-2 logarithm of `y` using `np.log2()`.
11. Compute $\log(1 + x)$ accurately for small $x$ using `np.log1p()`.
12. Compute $\exp(x) - 1$ accurately for small $x$ using `np.expm1()`.
13. Compute the absolute values of `np.array([-5, 3, -2, 0])` using `np.abs()`.
14. Compute the sine of angles (in radians) using `np.sin()`.
15. Compute the cosine of angles using `np.cos()`.
16. Compute the tangent of angles using `np.tan()`.
17. Convert an array of angles from degrees to radians using `np.radians()`.
18. Convert an array of angles from radians to degrees using `np.degrees()`.
19. Compute the hypotenuse $\sqrt{x^2 + y^2}$ element-wise using `np.hypot(x, y)`.
20. Check whether an object is an instance of `np.ufunc` using `isinstance(np.add, np.ufunc)`.


## Intermediate: Ufunc Methods (reduce, accumulate, outer, at)

Use:
```python
arr = np.array([1, 2, 3, 4, 5])
mat = np.arange(1, 13).reshape(3, 4)
```

21. Compute the sum of all elements in `arr` using `np.add.reduce(arr)`.
22. Compute the product of all elements in `arr` using `np.multiply.reduce(arr)`.
23. Compute the cumulative sum of `arr` using `np.add.accumulate(arr)`.
24. Compute the cumulative product of `arr` using `np.multiply.accumulate(arr)`.
25. Compute the pairwise addition table between `a = [1, 2, 3]` and `b = [10, 20, 30]` using `np.add.outer(a, b)`.
26. Compute the multiplication table between two vectors using `np.multiply.outer(a, b)`.
27. Compute pairwise absolute differences $|a_i - b_j|$ using `np.subtract.outer(a, b)` and `np.abs()`.
28. Perform unbuffered in-place addition at duplicate indices using `np.add.at()`.
29. Explain why `arr[[0, 0, 1]] += 1` increments index 0 only once, whereas `np.add.at(arr, [0, 0, 1], 1)` increments index 0 twice.
30. Perform unbuffered in-place subtraction at specified indices using `np.subtract.at()`.
31. Reduce along axis 0 of `mat` using `np.add.reduce(mat, axis=0)`.
32. Reduce along axis 1 of `mat` using `np.multiply.reduce(mat, axis=1)`.
33. Reduce across rows while retaining dimensions using `np.add.reduce(mat, axis=1, keepdims=True)`.
34. Find the cumulative minimum along each row using `np.minimum.accumulate(mat, axis=1)`.
35. Find the cumulative maximum along each column using `np.maximum.accumulate(mat, axis=0)`.
36. Compute element-wise maximum between two arrays using `np.maximum(x, y)`.
37. Compute element-wise minimum between two arrays using `np.minimum(x, y)`.
38. Explain the difference between `np.maximum(x, y)` and `np.fmax(x, y)` when NaN values are present.
39. Explain the difference between `np.minimum(x, y)` and `np.fmin(x, y)` with NaNs.
40. Use `np.add.reduceat()` to compute partial sums over specified index slices `[0, 2, 4]`.


## Custom Vectorization with np.vectorize & np.frompyfunc

Use:
```python
def my_func(a, b):
    if a > b:
        return a - b
    else:
        return a + b
```

41. Vectorize the scalar function `my_func` using `np.vectorize()`.
42. Evaluate the vectorized function on two 1D NumPy arrays of length 5.
43. Specify explicit output types in `np.vectorize()` using parameter `otypes=[float]`.
44. Create a universal function from a Python callable using `np.frompyfunc(my_func, nin=2, nout=1)`.
45. Explain why `np.frompyfunc()` returns an array with `dtype=object` and how to cast it to float.
46. Benchmark the execution time of Python list comprehension vs `np.vectorize` vs pure NumPy array expressions.
47. Explain why `np.vectorize()` is a syntactic convenience and does not provide native C-speed acceleration.
48. Vectorize a function that takes an array slice as an input argument using signature specifications in `np.vectorize(signature=...)`.
49. Create a vectorized function that computes the Levenshtein distance between pairs of string arrays.
50. Vectorize a conditional piecewise mathematical formula: $f(x) = x^2$ if $x > 0$ else $-x$.


## In-place Outputs & Memory Re-use with `out=`

Use:
```python
A = np.ones((5, 5))
B = np.full((5, 5), 2.0)
out_buf = np.empty((5, 5))
```

51. Add `A` and `B` storing the result directly into pre-allocated `out_buf` using `np.add(A, B, out=out_buf)`.
52. Verify that the memory address of `out_buf` is identical before and after calling `np.add(out=out_buf)`.
53. Perform in-place multiplication of array `A` by 3 using `np.multiply(A, 3, out=A)`.
54. Perform element-wise division storing output in `A` in-place without creating intermediate arrays.
55. Compute the exponential of array `A` in-place using `np.exp(A, out=A)`.
56. Use the `where=` keyword parameter in `np.divide()` to safely divide arrays while avoiding division by zero: `np.divide(x, y, out=np.zeros_like(x), where=(y != 0))`.
57. Compute square root only on non-negative elements using `np.sqrt(x, out=np.zeros_like(x), where=(x >= 0))`.
58. Compute reciprocal ($1/x$) safely with `np.reciprocal(x, out=np.zeros_like(x), where=(x != 0))`.
59. Use `where=` to apply in-place addition only to even elements of an array.
60. Chain multiple in-place ufunc operations into a pre-allocated buffer to eliminate memory overhead.


## Advanced: Bitwise, Comparison & Special Floating-Point Ufuncs

61. Perform bitwise AND between two integer arrays using `np.bitwise_and()`.
62. Perform bitwise OR between two integer arrays using `np.bitwise_or()`.
63. Perform bitwise XOR between two integer arrays using `np.bitwise_xor()`.
64. Perform bitwise NOT (inversion) using `np.bitwise_not()` or `np.invert()`.
65. Perform left bit-shift using `np.left_shift(x, 2)`.
66. Perform right bit-shift using `np.right_shift(x, 1)`.
67. Perform element-wise equality test returning a boolean array using `np.equal()`.
68. Perform element-wise not-equal test using `np.not_equal()`.
69. Perform element-wise greater-than test using `np.greater()`.
70. Perform element-wise less-than-or-equal test using `np.less_equal()`.
71. Check element-wise float closeness within relative and absolute tolerances using `np.isclose()`.
72. Check if all elements in two float arrays are approximately equal using `np.allclose()`.
73. Decompose floating-point numbers into mantissa and exponent using `np.frexp()`.
74. Construct float numbers from mantissa and exponent using `np.ldexp()`.
75. Split float numbers into integer and fractional parts using `np.modf()`.
76. Compute the sign of each element (-1, 0, or 1) using `np.sign()`.
77. Compute copysign: assign the sign of array `y` to the magnitude of array `x` using `np.copysign(x, y)`.
78. Check if float elements are `NaN` using `np.isnan()`.
79. Check if float elements are infinite using `np.isinf()`.
80. Check if float elements are finite using `np.isfinite()`.


## 3D & Tensor Vectorization

Use:
```python
T1 = np.ones((2, 3, 4))
T2 = np.full((2, 3, 4), 5.0)
```

81. Perform element-wise multiplication of `T1` and `T2` using `np.multiply()`.
82. Reduce `T1` along axis 2 using `np.add.reduce(T1, axis=2)`.
83. Compute cumulative sum along axis 1 of `T1` using `np.add.accumulate(T1, axis=1)`.
84. Apply `np.sin()` across all elements of a 4D tensor.
85. Apply in-place clipping on a 3D tensor: `np.clip(T1, 0, 10, out=T1)`.
86. Broadcast a 1D vector of shape `(4,)` across `T1` using `np.add(T1, vec)`.
87. Compute outer subtraction between a 2D matrix and a 1D vector using `np.subtract.outer()`.
88. Compute tensor element-wise power using `np.power(T1, 3)`.
89. Check closeness between two 3D tensors using `np.allclose(T1, T2)`.
90. Use `np.maximum.reduce()` across axis 0 to compute element-wise maximum across multiple 2D matrices.


## Challenge Questions: Custom Fast Vectorized Algorithms

91. **Numerical Softmax Vectorization**: Implement a numerically stable softmax function $\sigma(z)_i = \frac{\exp(z_i - \max(z))}{\sum \exp(z_j - \max(z))}$ using NumPy ufuncs.
92. **Vectorized Sigmoid & ReLU**: Implement the Sigmoid activation $\sigma(x) = \frac{1}{1 + e^{-x}}$ and ReLU activation $\max(0, x)$ using ufuncs.
93. **Polynomial Evaluation (Horner's Method)**: Evaluate a polynomial $p(x) = c_0 + c_1 x + \dots + c_n x^n$ at an array of points $x$ using `np.multiply.accumulate()` or Horner's rule.
94. **Pairwise Manhattan Distance Grid**: Compute the $L_1$ distance grid between two point sets using `np.subtract.outer()` and `np.abs.reduce()`.
95. **Gini Impurity Calculation**: Vectorize the Gini impurity calculation $1 - \sum p_i^2$ for class probability distribution arrays.
96. **Log-Sum-Exp Trick**: Implement a numerically stable Log-Sum-Exp function $\text{LSE}(x) = m + \log\left(\sum e^{x_i - m}\right)$ where $m = \max(x)$ using ufuncs.
97. **Vectorized Numerical Gradient**: Compute the central difference approximation of a derivative $f'(x) \approx \frac{f(x + h) - f(x - h)}{2h}$ using array slicing and subtraction.
98. **Heaviside Step Function**: Implement the Heaviside step function $H(x)$ with custom value at $x = 0$ using `np.heaviside()`.
99. **Running Window Maximum via Stride Reduction**: Compute running window maximums using strided views and `np.maximum.reduce()`.
100. **Fast Binned Accumulation via ufunc.at**: Given coordinates and values, accumulate values into a discrete 2D spatial grid using `np.add.at()`.

---

Try solving as many questions as possible using NumPy universal functions (`add`, `multiply`, `exp`, `log`, `sin`), ufunc methods (`reduce`, `accumulate`, `outer`, `at`), and `out=` / `where=` parameters without using Python `for` loops.
