# Arithmetic Question Bank Compiled by AutoMind Team

## Beginner: 1D Array Arithmetic

Use these arrays for Questions 1–10:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import numpy as np                                         %
%                                                            %
% a = np.array([10, 20, 30, 40, 50, 60, 70, 80, 90, 100])    %
% b = np.array([ 1,  2,  3,  4,  5,  6,  7,  8,  9,  10])    %
%                                                            %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Add scalar 5 to every element in array `a`.
2. Subtract scalar 15 from every element in array `a`.
3. Multiply every element in array `a` by 3.
4. Divide every element in array `a` by 2 (floating-point division).
5. Perform element-wise addition of array `a` and array `b`.
6. Subtract array `b` from array `a` element-wise.
7. Multiply array `a` and array `b` element-wise.
8. Divide array `a` by array `b` element-wise.
9. Perform floor division (integer division) of `a` by `b`.
10. Calculate the remainder (modulo) when elements of `a` are divided by 7.


## Intermediate: 1D Arithmetic & Universal Functions

Use:
```python
arr = np.arange(1, 21)
```

11. Square every element in `arr`.
12. Compute the square root of every element in `arr`.
13. Compute the cube (power of 3) of every element in `arr`.
14. Compute the exponential (e^x) for each element in `arr`.
15. Compute the natural logarithm (\ln(x)) of each element in `arr`.
16. Compute the reciprocal (1/x) of each element in `arr`.
17. Find the remainder of each element in `arr` when divided by 4.
18. Negate all values in `arr` (multiply each element by -1).
19. Double the values of the first half of `arr` and halve the values of the second half.
20. Add the elements of `arr` with its reversed version using element-wise addition.


## 2D Array Arithmetic

Use these arrays for Questions 21–35:

```python
A = np.array([
    [ 2,  4,  6,  8, 10],
    [12, 14, 16, 18, 20],
    [22, 24, 26, 28, 30],
    [32, 34, 36, 38, 40],
    [42, 44, 46, 48, 50]
])

B = np.array([
    [ 1,  2,  3,  4,  5],
    [ 6,  7,  8,  9, 10],
    [11, 12, 13, 14, 15],
    [16, 17, 18, 19, 20],
    [21, 22, 23, 24, 25]
])
```

21. Add matrix `A` and matrix `B` element-wise.
22. Subtract matrix `B` from matrix `A`.
23. Perform element-wise multiplication of `A` and `B` (Hadamard product).
24. Divide matrix `A` by matrix `B` element-wise.
25. Multiply matrix `A` by scalar 0.5.
26. Raise every element in matrix `B` to the power of 2.
27. Compute the matrix product of `A` and `B` using the `@` operator or `np.matmul()`.
28. Compute the sum of all elements in matrix `A`.
29. Compute the sum of each row in matrix `A` (row-wise sum).
30. Compute the sum of each column in matrix `A` (column-wise sum).
31. Compute the mean of each row in matrix `B`.
32. Compute the mean of each column in matrix `B`.
33. Compute the cumulative sum of matrix `A` along each column.
34. Subtract the global minimum of matrix `A` from all of its elements.
35. Generate a binary array (with values 1 and 0) where `A > B` element-wise.


## Advanced 2D Arithmetic & Broadcasting

36. Add a 1D array `v = np.array([1, 2, 3, 4, 5])` to every row of matrix `A` using broadcasting.
37. Multiply every column of matrix `A` by a 1D column vector `col = np.array([[1], [2], [3], [4], [5]])`.
38. Subtract the row-wise mean from each corresponding row of matrix `A` (row centering).
39. Subtract the column-wise mean from each corresponding column of matrix `B` (column centering).
40. Divide each row of matrix `A` by its corresponding row sum so that each row sums to 1.
41. Scale all elements of matrix `A` between 0 and 1 using Min-Max scaling: $\frac{A - \min(A)}{\max(A) - \min(A)}$.
42. Standardize matrix `B` (Z-score normalization: subtract the global mean and divide by the standard deviation).
43. Add a row vector of shape `(1, 5)` and a column vector of shape `(5, 1)` to generate a 5×5 addition grid.
44. Perform an in-place addition of matrix `B` into matrix `A` without creating a new array in memory.
45. Compute the outer product of `u = np.arange(1, 6)` and `v = np.arange(1, 6)` using broadcasting.


## 3D Array Arithmetic

Use:
```python
arr = np.arange(1, 25).reshape(2, 3, 4)

# array has shape (2, 3, 4)
```

46. Multiply every element in `arr` by 10.
47. Add a 1D vector of shape `(4,)` across the last dimension of `arr` using broadcasting.
48. Add a column vector of shape `(3, 1)` across each 2D slice of `arr`.
49. Compute the sum along axis 0, collapsing the 3D array into a 2D array of shape `(3, 4)`.
50. Compute the mean along axis 1 (across rows), resulting in an array of shape `(2, 4)`.


## Challenge Questions

51. Compute the Euclidean distance between two vectors `u = np.array([1, 2, 3, 4, 5])` and `v = np.array([6, 7, 8, 9, 10])` using only vectorized arithmetic operations and `np.sum()`.
52. Given an array with positive and negative numbers, replace all negative values with 0 using only arithmetic operations and boolean masks (without `np.where` or `if` statements).
53. Compute the pairwise absolute difference matrix $|x_i - x_j|$ for all pairs in `x = np.array([2, 5, 8, 11])` using broadcasting.
54. Given a matrix, normalize each row by dividing each row by its Euclidean norm ($L_2$ norm) so each row has unit length.
55. Compute the weighted average of each column of matrix `A` given weights `w = np.array([0.1, 0.2, 0.3, 0.2, 0.2])` along the rows without using loops.

---

Try solving as many questions as possible using vectorized NumPy arithmetic operators (`+`, `-`, `*`, `/`, `//`, `%`, `**`, `@`) and universal functions (e.g., `np.add`, `np.multiply`, `np.sum`, `np.mean`), without using Python loops.
