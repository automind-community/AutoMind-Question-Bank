# Random Numbers Question Bank Compiled by AutoMind Team

## Beginner: Basic Random Generation & Uniform Numbers

Use this setup for Questions 1–20:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import numpy as np                                         %
%                                                            %
% rng = np.random.default_rng(seed=42)                       %
%                                                            %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Initialize a modern NumPy random generator with a fixed seed of 42.
2. Generate an array of 10 random float numbers uniformly distributed in the half-open interval $[0.0, 1.0)$ using `rng.random()`.
3. Generate a 2D array of shape `(4, 5)` containing random floats in $[0.0, 1.0)$.
4. Generate an array of 8 random integers between 1 and 100 (inclusive) using `rng.integers()`.
5. Generate a 3×3 matrix of random integers between 0 and 9 (inclusive).
6. Generate 10 random floating-point numbers uniformly distributed in the range $[10.0, 50.0)$ using `rng.uniform()`.
7. Generate a single random float number between -1.0 and 1.0.
8. Explain the key advantages of the modern Generator API (`np.random.default_rng()`) over legacy functions (`np.random.seed()` and `np.random.rand()`).
9. Create two independent generators with identical seeds and verify that they produce the exact same sequence of numbers.
10. Generate an array of 1,000 random integers with values 0 or 1 (simulating 1,000 fair coin tosses).
11. Generate a 1D array of 20 random integers between -50 and 50.
12. Generate a random boolean array of shape `(5, 5)` with equal probability of `True` and `False`.
13. Generate 15 random floats in $[0, 1)$ with `dtype=np.float32` instead of default 64-bit float.
14. Use `rng.integers()` with parameter `endpoint=True` to generate random integers between 1 and 6 (inclusive).
15. Spawn independent child generators from a single parent seed using `SeedSequence`.
16. Generate a 1D array of 10 random numbers, then reset the generator with the original seed and regenerate to show reproducibility.
17. Generate a 2D array of shape `(10, 2)` representing random $(x, y)$ coordinates inside the unit square $[0, 1] \times [0, 1]$.
18. Generate 5 random integers from the range $[0, 100)$ where the step size between valid choices is 5 (e.g., 0, 5, 10, ...).
19. Generate a 4-element 1D array of random bytes using `rng.bytes()`.
20. Check the minimum and maximum values of an array of 100,000 uniform draws to verify that bounds $[0, 1)$ are respected.


## Intermediate: Standard & Continuous Distributions

Use:
```python
rng = np.random.default_rng(seed=100)
```

21. Generate 100 random numbers drawn from a standard normal distribution ($\mu = 0, \sigma = 1$) using `rng.standard_normal()`.
22. Generate 50 random samples from a Gaussian distribution with mean $\mu = 25$ and standard deviation $\sigma = 5$ using `rng.normal()`.
23. Generate a 2D array of shape `(5, 5)` sampled from a normal distribution with mean 0 and standard deviation 2.
24. Generate 100 samples from an Exponential distribution with scale parameter $\beta = 2.0$ (mean lifetime = 2.0) using `rng.exponential()`.
25. Generate 100 samples from a Log-Normal distribution with $\mu = 0$ and $\sigma = 0.5$ using `rng.lognormal()`.
26. Generate 50 samples from a Beta distribution with shape parameters $\alpha = 2$ and $\beta = 5$ using `rng.beta()`.
27. Generate 100 samples from a Gamma distribution with shape $k = 3.0$ and scale $\theta = 2.0$ using `rng.gamma()`.
28. Generate 50 samples from a Chi-Square distribution with 4 degrees of freedom using `rng.chisquare()`.
29. Generate 100 samples from Student's t-distribution with 10 degrees of freedom using `rng.standard_t()`.
30. Generate 50 samples from an F-distribution with degrees of freedom $df_1 = 5$ and $df_2 = 10$ using `rng.f()`.
31. Generate 100 samples from a Weibull distribution with shape parameter $a = 1.5$ using `rng.weibull()`.
32. Generate 50 samples from a Pareto distribution with shape parameter $a = 3.0$ using `rng.pareto()`.
33. Generate 100 samples from a Triangular distribution with lower limit 0, peak at 5, and upper limit 10 using `rng.triangular()`.
34. Generate 50 samples from a Laplace (double exponential) distribution with location 0 and scale 1 using `rng.laplace()`.
35. Generate 100 samples from a Logistic distribution with mean 10 and scale 2 using `rng.logistic()`.
36. Generate 50 samples from a Gumbel distribution with location 0 and scale 1 using `rng.gumbel()`.
37. Generate 10,000 samples from a standard normal distribution and verify that empirical mean $\approx 0$ and empirical standard deviation $\approx 1$.
38. Generate 10,000 samples from a uniform distribution over $[10, 20)$ and verify that empirical mean $\approx 15$ and variance $\approx \frac{(20-10)^2}{12}$.
39. Calculate the 2.5th and 97.5th percentiles of 100,000 standard normal samples to empirically estimate the 95% coverage interval.
40. Compute the empirical skewness of 10,000 draws from an Exponential distribution ($\lambda = 1$) and compare with theoretical value of 2.


## Discrete Distributions & Categorical Events

Use:
```python
rng = np.random.default_rng(seed=2024)
```

41. Simulate rolling a fair 6-sided die 100 times and compute the frequency of each face (1 through 6).
42. Generate 100 samples from a Binomial distribution simulating 10 coin flips with probability $p = 0.5$ per trial using `rng.binomial()`.
43. Generate 50 samples from a Poisson distribution with arrival rate $\lambda = 4.0$ events per unit time using `rng.poisson()`.
44. Generate 100 samples from a Geometric distribution with success probability $p = 0.2$ using `rng.geometric()`.
45. Generate 50 samples from a Hypergeometric distribution (lottery model: total 50 items, 10 winning items, drawing 5 items) using `rng.hypergeometric()`.
46. Generate 50 samples from a Negative Binomial distribution with number of successes $n = 5$ and probability $p = 0.3$.
47. Simulate 100 rolls of an unfair die where face 6 is twice as likely as any other face.
48. Generate 50 draws from a Multinomial distribution simulating 20 rolls of a fair 6-sided die per experiment using `rng.multinomial()`.
49. Simulate the number of heads obtained in 1,000 experiments of 100 tosses of a biased coin ($p = 0.6$).
50. Generate 100 samples from a discrete uniform distribution over the set $\{10, 20, 30, 40, 50\}$.
51. Simulate a Bernoulli trial with success probability $p = 0.75$ using boolean casting of `rng.random()`.
52. Simulate customer arrivals at a store across 24 hours assuming an average arrival rate of 15 customers per hour using a Poisson process.
53. Simulate the number of defectives in a random sample of 50 items drawn from a batch of 500 items containing 30 defectives.
54. Count how many trials it takes until the first success occurs in 1,000 simulations of a geometric event ($p = 0.1$).
55. Compute the empirical probability of getting at least 7 heads out of 10 flips of a fair coin across 10,000 trials.


## Sampling, Shuffling, & Permutations

Use these variables for Questions 56–70:

```python
deck = np.arange(1, 53)
colors = np.array(['Red', 'Green', 'Blue', 'Yellow', 'Purple'])
matrix = np.arange(1, 26).reshape(5, 5)
```

56. Draw 5 random cards from `deck` without replacement using `rng.choice()`.
57. Draw 10 samples from `colors` with replacement (duplicates allowed).
58. Sample 20 items from `colors` with custom probabilities: `p = [0.4, 0.2, 0.2, 0.1, 0.1]`.
59. Shuffle the elements of a 1D array `arr = np.arange(10)` in-place using `rng.shuffle()`.
60. Create a randomly permuted copy of `deck` without modifying the original array using `rng.permutation()`.
61. Shuffle the rows of `matrix` in-place along axis 0.
62. Shuffle the columns of `matrix` in-place along axis 1.
63. Randomly select 3 unique rows from `matrix` without replacement.
64. Randomly select 2 unique columns from `matrix` without replacement.
65. Given a dataset of 100 sample indices `indices = np.arange(100)`, split them into an 80% train set and 20% test set using random permutation.
66. Generate a random lottery draw: pick 6 distinct numbers from 1 to 49 and sort them in ascending order.
67. Perform a random choice over a 2D matrix directly by choosing 4 random rows.
68. Generate a random boolean mask of shape `(10,)` where each element has a 30% chance of being `True`.
69. Permute the elements along each row of a 2D array independently using `rng.permuted(axis=1)`.
70. Explain the difference between `rng.shuffle(arr)` and `rng.permuted(arr)`.


## Multi-Dimensional Arrays & Matrix Generation

71. Generate a 4×4 random symmetric matrix $S$ such that $S = S^T$.
72. Generate a 4×4 random positive semi-definite matrix by computing $M M^T$, where $M$ is a random 4×4 Gaussian matrix.
73. Generate a random orthogonal 3×3 matrix using the QR decomposition (`np.linalg.qr`) of a random Gaussian matrix.
74. Generate 100 points uniformly distributed inside a circle of radius $R = 5$ using polar coordinates ($r = R\sqrt{u}, \theta = 2\pi v$).
75. Generate 100 points uniformly distributed on the surface of a 3D unit sphere ($x^2 + y^2 + z^2 = 1$).
76. Generate 500 samples from a 2D Multivariate Normal distribution with mean `[2.0, 3.0]` and covariance matrix `[[1.0, 0.6], [0.6, 2.0]]` using `rng.multivariate_normal()`.
77. Simulate a 1D random walk of 1,000 steps where each step is randomly $+1$ or $-1$ with equal probability, using `np.cumsum()`.
78. Simulate a 2D random walk of 500 steps in the Cartesian plane starting from `(0, 0)`.
79. Create a random sparse binary matrix of shape `(10, 10)` where exactly 15% of elements are 1 and the rest are 0.
80. Generate a random correlation matrix of size 3×3 (symmetric, 1s along the diagonal, values between -1 and 1).
81. Generate a 5×5 random upper-triangular matrix with zero diagonal entries.
82. Generate a 5×5 diagonal matrix with random eigenvalues sampled uniformly from $[1, 10]$.
83. Generate a random permutation matrix of shape `(5, 5)`.
84. Generate a random transition probability matrix of size 4×4 where each row sums to 1.
85. Simulate a Geometric Brownian Motion stock price path: $S_t = S_0 \exp\left((\mu - \frac{1}{2}\sigma^2)t + \sigma W_t\right)$ for 252 trading days.


## 3D & Multi-Batch Random Tensors

Use:
```python
shape = (4, 8, 8, 3) # Batch of 4 images, 8x8 pixels, 3 color channels (RGB)
```

86. Generate a batch of synthetic image tensors of shape `(4, 8, 8, 3)` with pixel values randomly sampled as integers between 0 and 255.
87. Add zero-mean Gaussian noise ($\sigma = 10.0$) to the synthetic image tensor and clip the final pixel values to $[0, 255]$.
88. Generate a random binary dropout mask of shape `(32, 64, 128)` where activations are dropped (set to 0) with probability $p = 0.2$.
89. Generate a 3D tensor of shape `(10, 5, 3)` containing random unit vectors (each 3D vector along the last axis has Euclidean norm = 1.0).
90. From a 3D tensor of shape `(100, 28, 28)`, randomly sample a mini-batch of 16 slices along axis 0 without replacement.
91. Initialize neural network layer weights of shape `(256, 128)` using He (Kaiming) normal initialization: $\mathcal{N}(0, \sqrt{2 / n_{\text{in}}})$.
92. Initialize neural network layer weights of shape `(256, 128)` using Glorot (Xavier) uniform initialization: $\mathcal{U}(-\sqrt{6/(n_{\text{in}} + n_{\text{out}})}, \sqrt{6/(n_{\text{in}} + n_{\text{out}})})$.


## Challenge Questions: Monte Carlo & Stochastic Simulations

93. **Monte Carlo Estimation of $\pi$**: Generate 1,000,000 random points $(x, y)$ uniformly in $[-1, 1] \times [-1, 1]$, determine the proportion that fall inside the unit circle ($x^2 + y^2 \le 1$), and approximate the value of $\pi$.
94. **Monte Carlo Integration**: Numerically evaluate the definite integral $\int_0^1 \exp(-x^2) \, dx$ using 500,000 uniform random samples.
95. **Bootstrap Resampling**: Given a 1D sample `data = np.array([12, 15, 18, 22, 25, 30, 35])`, generate 1,000 bootstrap resamples with replacement and compute the 95% empirical confidence interval for the sample mean.
96. **Birthday Paradox Simulation**: Estimate the empirical probability that in a room of 23 people, at least two people share the same birthday (simulate 10,000 trials).
97. **Correlated Variables via Cholesky Decomposition**: Given a desired covariance matrix $\Sigma$, generate two correlated Gaussian variables $X$ and $Y$ by multiplying standard normal noise with the lower triangular Cholesky factor $L$ ($\Sigma = L L^T$).
98. **Vectorized Rejection Sampling**: Implement vectorized rejection sampling to draw 10,000 samples from the non-standard probability density function $f(x) = \frac{3}{4}(1 - x^2)$ for $x \in [-1, 1]$ using a uniform proposal distribution.
99. **Markov Chain Simulation**: Given a 3-state transition matrix $P$, simulate a 1,000-step trajectory and compute the empirical stationary distribution.
100. **Gambler's Ruin Problem**: Simulate 1,000 rounds of a gambler starting with \$50, betting \$1 on fair coin tosses ($p = 0.5$), and determine the probability of reaching \$100 before going bankrupt (\$0).

---

Try solving as many questions as possible using NumPy's modern Generator API (`np.random.default_rng()`) and vectorized sampling functions (`integers`, `random`, `normal`, `choice`, `shuffle`, `permutation`) without using Python `for` loops.
