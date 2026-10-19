# Broadcasting Question Bank Compiled by AutoMind Team

## Beginner: 1D Broadcasting & Scalars

Use these variables for Questions 1–10:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import numpy as np                                         %
%                                                            %
% arr = np.array([10, 20, 30, 40, 50])                        %
% s = 5                                                      %
%                                                            %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Add scalar `s` to 1D array `arr` and explain how NumPy broadcasts the scalar.
2. Multiply `arr` by scalar `s` using broadcasting.
3. Convert `arr` from shape `(5,)` into a row vector of shape `(1, 5)` using `np.newaxis` or `None`.
4. Convert `arr` from shape `(5,)` into a column vector of shape `(5, 1)` using `np.newaxis` or `None`.
5. What is the resulting shape when broadcasting an array of shape `(5,)` with an array of shape `(1,)`?
6. Add array `arr` to a single-element array `c = np.array([100])` of shape `(1,)`.
7. Explain why broadcasting succeeds between shapes `(5,)` and `(1,)`, but fails between `(5,)` and `(4,)`.
8. Check if shapes `(5,)` and `(5, 1)` are broadcast-compatible, and determine the resulting shape.
9. Add `arr` of shape `(5,)` to its column vector version of shape `(5, 1)`. What is the resulting shape and structure?
10. Divide `arr` by scalar 2.0 without modifying the original array.


## Intermediate: 1D and 2D Array Broadcasting

Use:
```python
matrix = np.arange(1, 21).reshape(4, 5)
row = np.array([1, 2, 3, 4, 5])
col = np.array([10, 20, 30, 40])
```

11. Add `row` (shape `(5,)`) to every row of `matrix` (shape `(4, 5)`).
12. Reshape `col` so that it can be broadcast across each column of `matrix`.
13. Add the reshaped `col` to `matrix` along axis 1 (across columns).
14. Multiply each column of `matrix` by `row` using broadcasting.
15. Divide each row of `matrix` by the corresponding element in `col` using broadcasting.
16. Subtract the column-wise mean from `matrix` using `matrix.mean(axis=0)`.
17. Subtract the row-wise mean from `matrix` using `matrix.mean(axis=1, keepdims=True)`.
18. Normalize each row of `matrix` by dividing each row by its maximum value using `keepdims=True`.
19. Given `a = np.ones((4, 1))` and `b = np.zeros((1, 5))`, add them together. What are the resulting shape and values?
20. Determine if an array of shape `(4, 5)` can broadcast directly with an array of shape `(4,)`. If not, how must the second array be reshaped?


## 2D Array Broadcasting: Outer Operations & Grids

Use these arrays for Questions 21–35:

```python
x = np.array([1, 2, 3, 4, 5])
y = np.array([10, 20, 30, 40, 50])
```

21. Compute a 5×5 addition grid where element `(i, j)` is `x[i] + y[j]` using broadcasting.
22. Compute a 5×5 multiplication table of `x` and `y` using broadcasting without `np.outer()`.
23. Compute the pairwise difference table `x[i] - y[j]` for all elements of `x` and `y`.
24. Compute a 5×5 distance matrix showing $|x_i - x_j|$ for all pairs in `x`.
25. Given 2D array `grid = x[:, None] * y[None, :]`, extract the main diagonal elements.
26. Broadcast a 1D boolean mask `mask = np.array([True, False, True, False, True])` across all rows of `grid`.
27. Broadcast `mask` across all columns of `grid` by reshaping it to `(5, 1)`.
28. Using broadcasting, create a 2D boolean mask where `x[:, None] < y[None, :]`.
29. Create a 5×5 checkerboard pattern of alternating 0s and 1s using broadcasting on two 1D coordinate vectors.
30. Given `A = np.arange(12).reshape(3, 1, 4)` and `B = np.arange(8).reshape(1, 2, 4)`, predict the broadcast shape and compute `A + B`.
31. Given `P = np.ones((3, 4))` and `Q = np.ones((3, 1))`, perform element-wise subtraction `P - Q`.
32. What error occurs when attempting `np.ones((3, 4)) + np.ones((4, 3))`? Explain which broadcasting rule is violated.
33. Compute the outer product of `u = np.array([2, 4, 6])` and `v = np.array([1, 3, 5, 7])` using `None` indexing.
34. Center `grid` by subtracting its global mean using scalar broadcasting.
35. Min-max scale each column of `grid` independently between 0 and 1 using `grid.min(axis=0)` and `grid.max(axis=0)` with broadcasting.


## Advanced 2D & 3D Broadcasting

36. Add a 1D vector `w = np.array([1, 2, 3])` of shape `(3,)` to a 3D array of shape `(2, 4, 3)`.
37. Add a vector `v = np.array([10, 20, 30, 40])` of shape `(4,)` to a 3D array of shape `(2, 4, 3)`. How must `v` be reshaped?
38. Given an RGB image array `img` of shape `(100, 100, 3)`, adjust the brightness of the R, G, and B channels independently using a factor array `factors = np.array([1.2, 0.9, 0.8])`.
39. Given a batch of grayscale images `batch` of shape `(32, 64, 64)`, subtract a per-image mean of shape `(32, 1, 1)` from each image.
40. Use `np.broadcast_to()` to broadcast a 1D array `a = np.array([1, 2, 3])` to shape `(4, 3)` without copying data in memory.
41. Inspect the `.strides` of the array created by `np.broadcast_to()` and explain why the stride for the broadcasted axis is 0.
42. Use `np.broadcast_arrays()` to explicitly obtain the broadcasted views of `x = np.arange(3).reshape(3, 1)` and `y = np.arange(4)`.
43. Given two matrices `A` of shape `(10, 3)` and `B` of shape `(15, 3)` representing 3D coordinates, expand dimensions to broadcast them into shape `(10, 15, 3)`.
44. Compute pairwise squared Euclidean distances $(A_i - B_j)^2$ summed over coordinates between `A` of shape `(10, 3)` and `B` of shape `(15, 3)` to yield a `(10, 15)` distance matrix.
45. Perform batch matrix outer products: broadcast batch vectors of shape `(B, N, 1)` and `(B, 1, M)` to compute outer products for each batch sample, yielding shape `(B, N, M)`.


## 3D Array & Multi-Dimensional Broadcasting

Use:
```python
tensor = np.arange(1, 25).reshape(2, 3, 4)

# tensor has shape (2, 3, 4)
```

46. Add a 2D matrix of shape `(3, 4)` to `tensor` so that it is added to each 2D slice along axis 0.
47. Add a 2D matrix of shape `(2, 1)` to `tensor`. What shape must it have to broadcast along axis 0 and axis 1?
48. Divide `tensor` by a 1D array of shape `(4,)` across the last dimension.
49. Standardize `tensor` across the feature dimension (axis 2) by subtracting the mean and dividing by the standard deviation with `keepdims=True`.
50. Multiply `tensor` with a 3D mask of shape `(2, 1, 4)` and describe the broadcast behavior.


## Challenge Questions

51. **One-Hot Encoding**: Given a 1D array of class labels `labels = np.array([0, 2, 1, 3, 0])` and `num_classes = 4`, generate a one-hot encoded 2D array of shape `(5, 4)` using only broadcasting and the `==` operator.
52. **Gaussian RBF Kernel**: Given a 1D array of points `pts = np.array([1.0, 2.5, 4.0, 5.5])` and parameter $\gamma = 0.5$, compute the RBF kernel matrix $K_{ij} = \exp(-\gamma (x_i - x_j)^2)$ using broadcasting.
53. **Weighted Euclidean Distance**: Given coordinate matrices `X` of shape `(N, D)` and `Y` of shape `(M, D)`, and a feature weight vector `w` of shape `(D,)`, compute the weighted Euclidean distance matrix $\sqrt{\sum_k w_k (X_{ik} - Y_{jk})^2}$ of shape `(N, M)` in a single vectorized broadcasting expression.
54. **Bilinear 2D Grid Evaluation**: Evaluate the 2D function $f(x, y) = \sin(x) + \cos(y)$ over a grid where $x \in [0, \pi]$ (50 points) and $y \in [0, \pi]$ (50 points) using 1D arrays and broadcasting (without calling `np.meshgrid`).
55. **Broadcasting vs Tiling Memory Inspection**: Demonstrate why broadcasting `a[:, None] + b[None, :]` does not allocate memory for duplicated rows/columns compared to `np.tile()`, by inspecting `.nbytes` and `np.shares_memory()`.

---

Try solving as many questions as possible using NumPy's broadcasting rules and shape manipulation (e.g., `[:, None]`, `np.newaxis`, `reshape()`, `keepdims=True`) without using `for` loops or explicit tiling functions like `np.tile()` or `np.repeat()`.
