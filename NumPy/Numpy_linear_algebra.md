# Linear Algebra Question Bank Compiled by AutoMind Team

## Beginner: Dot Products, Vector Norms & Matrix Multiplication

Use this setup for Questions 1–20:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import numpy as np                                         %
%                                                            %
% u = np.array([1, 2, 3])                                    %
% v = np.array([4, 5, 6])                                    %
% A = np.array([[1, 2], [3, 4]])                             %
% B = np.array([[5, 6], [7, 8]])                             %
%                                                            %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Compute the dot product of vectors `u` and `v` using `np.dot()`.
2. Compute the dot product of `u` and `v` using the `@` operator.
3. Compute the inner product of `u` and `v` using `np.inner()`.
4. Compute the outer product of `u` and `v` using `np.outer()`.
5. Compute the cross product of 3D vectors `u` and `v` using `np.cross()`.
6. Compute the Euclidean norm ($L_2$ norm) of vector `u` using `np.linalg.norm()`.
7. Compute the Manhattan norm ($L_1$ norm) of vector `u` using `ord=1` in `np.linalg.norm()`.
8. Compute the maximum norm ($L_\infty$ norm) of vector `u` using `ord=np.inf`.
9. Perform matrix multiplication between `A` and `B` using `np.matmul()`.
10. Perform matrix multiplication between `A` and `B` using the `@` operator.
11. Multiply matrix `A` with column vector `x = np.array([1, 2])`.
12. Compute the trace (sum of diagonal elements) of matrix `A` using `np.trace()`.
13. Transpose matrix `A` using `.T`.
14. Compute the determinant of matrix `A` using `np.linalg.det()`.
15. Compute the matrix inverse of `A` using `np.linalg.inv()`.
16. Multiply `A` by its inverse $A^{-1}$ and verify that the result is an identity matrix (within float tolerance).
17. Check if matrix `A` is invertible by verifying its determinant is non-zero.
18. Compute the Frobenius norm of matrix `A` using `np.linalg.norm()`.
19. Compute the $L_1$ induced matrix norm of `A` (maximum absolute column sum) using `ord=1`.
20. Compute the $L_\infty$ induced matrix norm of `A` (maximum absolute row sum) using `ord=np.inf`.


## Intermediate: Solving Linear Systems & Matrix Decompositions

Use:
```python
A = np.array([
    [3.0, 1.0, 2.0],
    [1.0, 4.0, 1.0],
    [2.0, 1.0, 5.0]
])
b = np.array([9.0, 12.0, 15.0])
```

21. Solve the system of linear equations $Ax = b$ for vector $x$ using `np.linalg.solve()`.
22. Verify the solution by computing $Ax - b$ and checking if the residual is near zero using `np.allclose()`.
23. Solve the same linear system by explicitly computing $x = A^{-1}b$ and explain why `np.linalg.solve()` is numerically superior.
24. Compute the condition number of matrix `A` using `np.linalg.cond()`.
25. What does a large condition number imply about the numerical stability of solving $Ax = b$?
26. Compute the matrix rank of `A` using `np.linalg.matrix_rank()`.
27. Check whether a 3×3 matrix is full-rank.
28. Compute the eigenvalues and right eigenvectors of matrix `A` using `np.linalg.eig()`.
29. Verify the eigenvalue equation $A v = \lambda v$ for the first eigenvalue-eigenvector pair.
30. Given a symmetric matrix $S = A + A^T$, compute its eigenvalues and eigenvectors using `np.linalg.eigh()`.
31. Explain why `np.linalg.eigh()` is preferred over `np.linalg.eig()` for symmetric/Hermitian matrices.
32. Compute the eigenvalues only (without eigenvectors) using `np.linalg.eigvals()`.
33. Compute only the eigenvalues of a symmetric matrix using `np.linalg.eigvalsh()`.
34. Perform the Cholesky decomposition $A = L L^T$ of a symmetric positive-definite matrix using `np.linalg.cholesky()`.
35. Reconstruct the original matrix from its lower-triangular Cholesky factor $L$ using $L @ L.T$.
36. Perform QR decomposition $A = Q R$ using `np.linalg.qr()`.
37. Verify that the $Q$ matrix from QR decomposition is orthogonal by checking $Q^T Q \approx I$.
38. Verify that the $R$ matrix from QR decomposition is upper triangular.
39. Compute the reduced/economic QR decomposition for a rectangular matrix of shape `(5, 3)` using `mode='reduced'`.
40. Compute the complete QR decomposition for a rectangular matrix using `mode='complete'`.


## Singular Value Decomposition (SVD) & Pseudo-Inverse

Use:
```python
M = np.array([
    [1.0, 2.0, 3.0],
    [4.0, 5.0, 6.0],
    [7.0, 8.0, 9.0],
    [10.0, 11.0, 12.0]
])
```

41. Compute the Singular Value Decomposition $M = U \Sigma V^T$ using `np.linalg.svd()`.
42. What are the shapes of $U$, $S$ (singular values), and $Vh$ ($V^T$) returned by `np.linalg.svd()`?
43. Compute the economy/reduced SVD using `full_matrices=False`.
44. Reconstruct the original matrix `M` from the reduced $U$, $S$, and $Vh$ using matrix multiplication.
45. Compute only the singular values of `M` without computing singular vectors using `compute_uv=False`.
46. Compute the Moore-Penrose pseudo-inverse of `M` using `np.linalg.pinv()`.
47. Compute the Moore-Penrose pseudo-inverse of a square singular matrix.
48. Verify the pseudo-inverse property $M M^+ M \approx M$.
49. Solve an overdetermined system $M x \approx y$ using the pseudo-inverse $x = M^+ y$.
50. Solve a linear least-squares problem $M x \approx y$ using `np.linalg.lstsq()`.
51. Extract the least-squares residual and rank returned by `np.linalg.lstsq()`.
52. Perform rank-1 low-rank matrix approximation of `M` using the largest singular value and its singular vectors.
53. Perform rank-2 approximation of a matrix using the top 2 singular values.
54. Calculate the nuclear norm (sum of singular values) of matrix `M`.
55. Compute the spectral norm (largest singular value) of matrix `M` using `ord=2` in `np.linalg.norm()`.
56. Check whether all singular values are non-negative and sorted in descending order.
57. Count how many non-zero singular values exist to determine the numerical rank of `M`.
58. Compute the energy (proportion of total variance) captured by the top $k$ singular values: $\sum_{i=1}^k \sigma_i^2 / \sum \sigma_i^2$.
59. Whiten a data matrix $X$ using SVD / PCA whitening.
60. Compute the projection of data matrix $X$ onto its first two principal components using $V^T$.


## Advanced: Matrix Powers, Exponential & Tensor Contractions

61. Compute the matrix power $A^3 = A @ A @ A$ using `np.linalg.matrix_power()`.
62. Compute the inverse of matrix $A$ using `np.linalg.matrix_power(A, -1)`.
63. Compute $A^0$ using `np.linalg.matrix_power()` and verify it yields the identity matrix.
64. Compute the Kronecker product of two 2×2 matrices using `np.kron()`.
65. Compute tensor dot product along specified axes using `np.tensordot()`.
66. Contract two 3D tensors along their last two dimensions using `np.tensordot(T1, T2, axes=2)`.
67. Perform matrix multiplication between two 2D matrices using `np.einsum('ij,jk->ik', A, B)`.
68. Compute the vector dot product using Einstein summation: `np.einsum('i,i->', u, v)`.
69. Compute the trace of matrix $A$ using `np.einsum('ii->', A)`.
70. Extract the diagonal of matrix $A$ using `np.einsum('ii->i', A)`.
71. Compute outer product $u \otimes v$ using `np.einsum('i,j->ij', u, v)`.
72. Compute batch matrix multiplication for tensors of shape `(B, N, K)` and `(B, K, M)` using `np.einsum('bik,bkm->bim', X, Y)`.
73. Transpose a 3D tensor using `np.einsum('ijk->kji', T)`.
74. Compute sum of all elements in a 3D tensor using `np.einsum('ijk->', T)`.
75. Compute row sums of matrix $A$ using `np.einsum('ij->i', A)`.
76. Compute column sums of matrix $A$ using `np.einsum('ij->j', A)`.
77. Calculate the quadratic form $x^T A x$ using `np.einsum('i,ij,j->', x, A, x)`.
78. Multiply a batch of matrices `(B, N, N)` by a single matrix `(N, N)` using Einstein summation.
79. Compute pairwise dot products between two sets of vectors of shape `(N, D)` and `(M, D)` using `einsum`.
80. Calculate matrix polynomial $p(A) = 2A^2 - 3A + 5I$ using matrix arithmetic.


## Batch Linear Algebra & 3D Tensors

Use:
```python
batch_A = np.random.default_rng(42).normal(size=(10, 3, 3))
batch_b = np.random.default_rng(42).normal(size=(10, 3, 1))
```

81. Compute the determinants of all 10 matrices in `batch_A` in a single vectorized call using `np.linalg.det()`.
82. Compute the inverses of all 10 matrices in `batch_A` simultaneously using `np.linalg.inv()`.
83. Solve all 10 linear systems $A_i x_i = b_i$ in parallel using `np.linalg.solve(batch_A, batch_b)`.
84. Compute the eigenvalues for each matrix in `batch_A` simultaneously using `np.linalg.eig()`.
85. Compute the SVD for all 10 matrices in `batch_A` using a single call to `np.linalg.svd()`.
86. Compute the Frobenius norms of each matrix in `batch_A` along axes `(-2, -1)`.
87. Compute the matrix rank for each matrix in a batch of shape `(10, 4, 4)` using `np.linalg.matrix_rank()`.
88. Multiply a batch of matrices `batch_A` with a batch of matrices `batch_B` using `@` or `np.matmul()`.
89. Compute the trace of each matrix in a 3D batch using `np.trace(batch_A, axis1=1, axis2=2)`.
90. Verify that batch matrix inversion preserves shape `(B, N, N)`.


## Challenge Questions: Applied Linear Algebra & Numerical Algorithms

91. **Ordinary Least Squares (OLS) Linear Regression**: Given feature matrix $X \in \mathbb{R}^{N \times D}$ and target vector $y \in \mathbb{R}^N$, compute the closed-form OLS weights $\hat{w} = (X^T X)^{-1} X^T y$ using `np.linalg.solve()`.
92. **Ridge Regression (L2 Regularization)**: Compute regularized weights $\hat{w}_{\text{ridge}} = (X^T X + \lambda I)^{-1} X^T y$ without inverting $X^T X + \lambda I$ directly.
93. **Principal Component Analysis (PCA)**: Center a data matrix $X$, compute its covariance matrix, find the eigenvectors, and project data onto the top 2 principal components.
94. **Power Iteration Method**: Implement the power iteration algorithm to find the dominant eigenvalue and eigenvector of a square matrix using a vectorized while-loop.
95. **Gram-Schmidt Orthogonalization**: Implement the Gram-Schmidt process to orthogonalize the columns of a matrix using vector projections.
96. **Positive Definiteness Test**: Test whether a symmetric matrix is positive-definite by verifying that all its eigenvalues are strictly positive (or via Cholesky decomposition).
97. **Matrix Logarithm & Sqrt**: Compute the square root of a positive semi-definite matrix $S = V \Lambda^{1/2} V^T$ using its spectral decomposition.
98. **Procrustes Alignment**: Given two sets of corresponding 3D points $P$ and $Q$, find the optimal rotation matrix $R$ that aligns $P$ to $Q$ using SVD ($R = V U^T$).
99. **Distance-to-Hyperplane**: Compute the orthogonal distance from point $p$ to hyperplane $w^T x + b = 0$ using vector dot product and norm.
100. **Matrix Condition Estimation**: Generate a Hilbert matrix of size 10×10 and evaluate its condition number to demonstrate ill-conditioning.

---

Try solving as many questions as possible using `np.linalg` routines (`solve`, `inv`, `det`, `eig`, `eigh`, `svd`, `qr`, `cholesky`, `norm`, `lstsq`) and Einstein summation (`np.einsum`) without using Python `for` loops.
