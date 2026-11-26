# Advanced Operations & Performance Question Bank Compiled by AutoMind Team

## Beginner: Apply, Map, Pipe & Method Chaining

Use this setup for Questions 1–10:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import pandas as pd                                        %
% import numpy as np                                         %
%                                                            %
% df = pd.DataFrame({                                        %
%     'a': [1, 2, 3, 4, 5],                                  %
%     'b': [10, 20, 30, 40, 50],                             %
%     'label': ['low', 'mid', 'mid', 'high', 'high']         %
% })                                                         %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Apply a function across each column (`axis=0`) to compute `max - min` using `df[['a', 'b']].apply(lambda col: col.max() - col.min())`.
2. Apply a function across each row (`axis=1`) to compute `row['a'] * 2 + row['b']` using `df.apply(..., axis=1)`.
3. Map values of `'label'` using a dictionary `{'low': 1, 'mid': 2, 'high': 3}` via `df['label'].map()`.
4. Apply an element-wise function to every cell of a numeric `DataFrame` using `df[['a', 'b']].map(lambda x: x ** 2)` (note: `DataFrame.map` replaced `applymap` in Pandas 2.1).
5. Use `df.assign()` to add two new derived columns `'sum_ab'` and `'ratio'` cleanly in a method chain.
6. Use `df.pipe(func, arg=...)` to pass a `DataFrame` into a reusable custom transformation function inside a chain.
7. Chain `.assign()`, `.query()`, and `.sort_values()` in a single readable expression without intermediate variables.
8. Rename columns dynamically inside a method chain using `.rename(columns=str.upper)`.
9. Replace `df['a']` values in-place vs returning a new `DataFrame` and explain why Pandas recommends avoiding `inplace=True`.
10. Convert a `Series` of strings into integer factor codes and unique categories using `pd.factorize()`.


## Intermediate: Vectorization, Eval & Query Optimization

Use:
```python
rng = np.random.default_rng(42)
big = pd.DataFrame({
    'x': rng.normal(size=100_000),
    'y': rng.normal(size=100_000),
    'z': rng.integers(0, 100, size=100_000),
    'cat': rng.choice(['A', 'B', 'C', 'D'], size=100_000)
})
```

11. Benchmark row-wise `df.apply(..., axis=1)` vs vectorized arithmetic `(big['x'] + big['y']) * big['z']` and explain the speedup.
12. Replace a slow `iterrows()` loop that computes conditional labels with vectorized `np.where()` or `np.select()`.
13. Explain why `itertuples(index=False)` is significantly faster than `iterrows()` when row iteration is unavoidable.
14. Use `pd.eval()` (or `big.eval('w = (x + y) * z')`) to evaluate arithmetic expressions with reduced intermediate memory allocation.
15. Compare `big.query('x > 0 and y < 0')` against standard boolean indexing `big[(big['x'] > 0) & (big['y'] < 0)]`.
16. Use `numexpr` (when installed) via `big.eval(..., engine='numexpr')` for multi-threaded expression evaluation.
17. Vectorize a lookup between two columns using `np.choose` or array indexing instead of `.apply(axis=1)`.
18. Use `.to_numpy()` to extract raw NumPy arrays for tight inner-loop linear algebra or Euclidean distance calculations.
19. Avoid repeated `pd.concat()` inside a loop; instead, collect DataFrames in a Python list and call `pd.concat()` once at the end.
20. Use `isin()` backed by a Python `set` instead of a large `list` for faster membership checks.


## Memory Optimization & Backends

Use the same `big` DataFrame for Questions 21–30:

21. Measure exact memory usage of each column in `big` (including `object` strings) using `big.memory_usage(deep=True)`.
22. Convert `'cat'` from `object` dtype to `category` dtype and measure the memory reduction.
23. Downcast `'z'` from `int64` to `uint8` (or `int8`) using `pd.to_numeric(..., downcast='unsigned')` or `.astype('int8')`.
24. Downcast `'x'` and `'y'` from `float64` to `float32` and verify the 50% memory savings.
25. Convert a DataFrame with mostly `0`s into a sparse representation using `df.astype(pd.SparseDtype('float64', 0))`.
26. Check the sparse density ratio using `s.sparse.density`.
27. Enable PyArrow-backed dtypes via `pd.options.mode.dtype_backend = 'pyarrow'` or `.astype('string[pyarrow]')` and compare string memory usage against `object`.
28. Enable Pandas Copy-on-Write (`pd.options.mode.copy_on_write = True`) and explain how it eliminates unnecessary defensive copies.
29. Configure display options temporarily using `with pd.option_context('display.max_columns', None, 'display.precision', 2):`.
30. Reset all modified Pandas options back to defaults using `pd.reset_option('all')`.


## Styling, Plotting & Testing

Use:
```python
summary = pd.DataFrame({
    'dept': ['Eng', 'Sales', 'HR', 'Marketing'],
    'revenue': [450000, 320000, 120000, 210000],
    'margin': [0.32, 0.24, 0.15, 0.28]
})
```

31. Highlight the maximum value in each numeric column in light green using `summary.style.highlight_max(color='lightgreen')`.
32. Apply a color gradient across `'revenue'` using `summary.style.background_gradient(subset=['revenue'], cmap='Blues')`.
33. Format `'revenue'` as currency (`$450,000`) and `'margin'` as percentages (`32.0%`) using `summary.style.format(...)`.
34. Render inline data bars inside `'revenue'` cells using `summary.style.bar(subset=['revenue'])`.
35. Create a bar chart of `'revenue'` by `'dept'` using `summary.plot(kind='bar', x='dept', y='revenue')`.
36. Create a histogram of `'x'` in `big` with 50 bins using `big['x'].plot(kind='hist', bins=50)`.
37. Create a box plot comparing `'x'` and `'y'` using `big[['x', 'y']].plot(kind='box')`.
38. Create a scatter plot of `'x'` vs `'y'` using `big.sample(500).plot(kind='scatter', x='x', y='y')`.
39. Assert that two DataFrames are identical (values, dtypes, index) in unit tests using `pd.testing.assert_frame_equal(df1, df2)`.
40. Assert that two Series are equal while ignoring dtype differences using `pd.testing.assert_series_equal(s1, s2, check_dtype=False)`.


## Custom Extensions & Advanced Internals

41. Register a custom DataFrame accessor `@pd.api.extensions.register_dataframe_accessor('custom')` to add domain-specific methods like `df.custom.summary()`.
42. Use `df.memory_usage().sum() / 1024**2` to report DataFrame footprint in megabytes (MB).
43. Explain the difference between `Index` (hash-table / binary-search backed) lookups and unindexed column scans.
44. Sort a DataFrame by an index before slicing ranges so `df.loc[start:end]` uses $O(\log N)$ binary search.
45. Use `pd.show_versions()` to inspect installed Pandas, NumPy, PyArrow, and optional dependency versions for bug reports.


## Challenge Questions: Production Performance & Architecture

46. **Zero-Loop Feature Engineering Pipeline**: Build a single `.pipe()`-based pipeline that cleans missing values, creates 3 derived features via `.assign()`, filters outliers, and normalizes numeric columns.
47. **80%+ Memory Compression Function**: Write a function `reduce_mem_usage(df)` that automatically downcasts every integer/float column to its smallest lossless dtype and converts low-cardinality strings (`nunique / len < 0.5`) to `category`.
48. **Vectorized Haversine Distance**: Given `lat1, lon1, lat2, lon2` columns in a 100k-row DataFrame, compute great-circle distance in kilometers using vectorized NumPy/Pandas trigonometry without `.apply()`.
49. **Fast Group-By Deduplication**: Given 1M rows with `(user_id, timestamp, value)`, find the latest row per `user_id` faster than `sort_values().drop_duplicates()` using `groupby('user_id')['timestamp'].idxmax()`.
50. **Custom `pd.testing` Diff Helper**: Write a test helper that compares two DataFrames ignoring row/column order (`check_like=True`) and floating-point noise (`rtol=1e-4`).

---

Try solving as many questions as possible using vectorized NumPy/Pandas operations, `.assign()`, `.pipe()`, `.eval()`, `pd.testing`, and dtype downcasting without Python `for` loops.
