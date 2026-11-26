# Series & DataFrame Creation Question Bank Compiled by AutoMind Team

## Beginner: Creating Series & Basic Inspection

Use this setup for Questions 1–10:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import pandas as pd                                        %
% import numpy as np                                         %
%                                                            %
% data = [10, 20, 30, 40, 50]                                %
% labels = ['a', 'b', 'c', 'd', 'e']                         %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Create a Pandas `Series` from the list `data` with default integer indexing.
2. Create a Pandas `Series` from `data` using `labels` as the custom index and `'scores'` as the `name`.
3. Create a `Series` from a Python dictionary `{'x': 100, 'y': 200, 'z': 300}` and observe how keys become the index.
4. Create a `Series` of length 5 filled with the scalar value `7.5` and index `labels`.
5. Create a `Series` from a NumPy array `np.arange(0, 10, 2)` with `dtype='float32'`.
6. Access the underlying NumPy array of a `Series` using `.to_numpy()` and its index using `.index`.
7. Check the data type, number of elements, and memory usage (in bytes) of a `Series` using `.dtype`, `.size`, and `.memory_usage()`.
8. Retrieve the first 3 elements and last 2 elements of a `Series` using `.head()` and `.tail()`.
9. Check whether all values in a `Series` are unique using `.is_unique` and whether the index is monotonically increasing using `.index.is_monotonic_increasing`.
10. Convert a `Series` back into a Python dictionary using `.to_dict()` and into a Python list using `.tolist()`.


## Intermediate: Creating DataFrames from Various Sources

Use:
```python
records_dict = {
    'name': ['Alice', 'Bob', 'Charlie', 'Diana'],
    'age': [25, 30, 35, 28],
    'city': ['NYC', 'LA', 'Chicago', 'Miami'],
    'salary': [70000.0, 82000.0, 95000.0, 68000.0]
}
```

11. Create a `DataFrame` from `records_dict` with default `RangeIndex`.
12. Create a `DataFrame` from `records_dict` using custom row labels `['emp1', 'emp2', 'emp3', 'emp4']`.
13. Create a `DataFrame` from `records_dict` while selecting only the columns `['name', 'salary']` via the `columns` parameter.
14. Create a `DataFrame` from a list of dictionaries `[{'a': 1, 'b': 2}, {'a': 3, 'c': 4}]` and observe how missing keys become `NaN`.
15. Create a `DataFrame` from a 2D NumPy array `np.arange(12).reshape(3, 4)` with column names `['C1', 'C2', 'C3', 'C4']` and row index `['R1', 'R2', 'R3']`.
16. Create a `DataFrame` from a dictionary of `Series` objects with partially overlapping indices.
17. Create a `DataFrame` using `pd.DataFrame.from_dict()` with `orient='index'` so dictionary keys become row labels.
18. Create a `DataFrame` from a list of tuples `[('Alice', 25), ('Bob', 30)]` using `pd.DataFrame.from_records()`.
19. Create an empty `DataFrame` with predefined columns `['id', 'timestamp', 'value']` and verify `.empty` is `True`.
20. Create a `DataFrame` from a 1D NumPy structured array with named fields `('id', 'i4')` and `('score', 'f8')`.


## DataFrame Inspection & Metadata

Use this DataFrame for Questions 21–30:

```python
df = pd.DataFrame({
    'product': ['Laptop', 'Mouse', 'Keyboard', 'Monitor', 'Desk'],
    'category': ['Tech', 'Tech', 'Tech', 'Tech', 'Furniture'],
    'price': [1200.0, 25.5, 75.0, 350.0, 450.0],
    'stock': [15, 120, 60, 22, 8],
    'in_stock': [True, True, True, True, True]
})
```

21. Display a concise summary of `df` including column dtypes, non-null counts, and memory usage using `df.info()`.
22. Generate summary statistics for all numeric columns using `df.describe()`.
23. Generate summary statistics for all columns (including object/boolean columns) using `df.describe(include='all')`.
24. Retrieve the dimensions `(rows, cols)`, total element count, and dimensionality of `df` using `.shape`, `.size`, and `.ndim`.
25. Display the column names as a Python list and the index object of `df`.
26. Return a random sample of 2 rows from `df` with a fixed `random_state=42` using `df.sample()`.
27. Check the data types of all columns using `df.dtypes` and count how many columns belong to each dtype using `.value_counts()`.
28. Select only numeric columns from `df` using `df.select_dtypes(include='number')`.
29. Exclude boolean and object columns from `df` using `df.select_dtypes(exclude=['bool', 'object'])`.
30. Inspect detailed per-column memory consumption (including deep object size) using `df.memory_usage(deep=True)`.


## Data Types, Nullable Dtypes & Type Conversion

Use:
```python
raw_df = pd.DataFrame({
    'id': ['1', '2', '3', '4'],
    'score': ['88.5', '92.0', 'invalid', '76.5'],
    'count': [10, 20, np.nan, 40],
    'active': [1, 0, 1, 1],
    'grade': ['A', 'B', 'A', 'C']
})
```

31. Convert the `'id'` column from string/object to `int64` using `.astype()`.
32. Convert the `'score'` column to numeric floats while coercing `'invalid'` to `NaN` using `pd.to_numeric(..., errors='coerce')`.
33. Convert `'count'` to Pandas nullable integer type `'Int64'` so `NaN` is preserved as `pd.NA` without casting to float.
34. Convert `'active'` to boolean dtype (`bool`) and `'grade'` to `category` dtype in a single `.astype({...})` call.
35. Automatically convert columns in `raw_df` to the best possible nullable dtypes using `raw_df.convert_dtypes()`.
36. Downcast a float64 column to the smallest possible float dtype (`float32`) using `pd.to_numeric(..., downcast='float')`.
37. Downcast an integer column to the smallest signed integer dtype using `pd.to_numeric(..., downcast='integer')`.
38. Create a `Series` using Pandas' nullable `pd.StringDtype()` (`dtype='string'`) and explain how it differs from `object` dtype.
39. Create a `Series` using PyArrow-backed dtype `dtype='int64[pyarrow]'` (if `pyarrow` is installed) and compare its NA handling.
40. Check whether a specific column has a numeric or categorical dtype using `pd.api.types.is_numeric_dtype()` and `isinstance(s.dtype, pd.CategoricalDtype)`.


## Advanced Constructors, Attributes & Copy Semantics

41. Create a `DataFrame` by transposing a dictionary of row-wise lists using `.T` and verify the resulting column dtypes.
42. Attach custom metadata (e.g., `df.attrs['source'] = 'sensor_v2'`) to a `DataFrame` and verify whether it persists after slicing.
43. Create a `DataFrame` from a generator expression yielding `(i, i**2, i**3)` for `i` in `range(10)` without first building a list.
44. Construct a `Series` from a scalar value `0` with a `MultiIndex` of 6 elements.
45. Create a shallow copy vs. a deep copy of a `DataFrame` using `df.copy(deep=False)` and `df.copy(deep=True)`, and test mutating a cell.


## Challenge Questions: Schema Design & Memory-Efficient Creation

46. **Cartesian Product DataFrame**: Given two lists `users = ['U1', 'U2', 'U3']` and `days = ['Mon', 'Tue', 'Wed']`, construct a `DataFrame` of all 9 `(user, day)` combinations using `pd.MultiIndex.from_product()`.
47. **Sparse DataFrame Creation**: Create a `DataFrame` of shape `(1000, 10)` that is 99% zeros using `pd.arrays.SparseArray` and compare its memory footprint to a dense `float64` DataFrame.
48. **Strict Schema Builder**: Write a constructor pattern that builds a `DataFrame` from raw dicts while enforcing exact column order, nullable dtypes (`Int64`, `string`, `boolean`), and missing column defaults.
49. **Diagonal & Identity DataFrame**: Construct a 5×5 identity `DataFrame` with matching row and column labels `['A', 'B', 'C', 'D', 'E']`.
50. **Copy-on-Write (CoW) Verification**: Explain and demonstrate what happens when modifying a slice `sub = df[['name', 'price']]; sub.iloc[0, 1] = 999` with `pd.options.mode.copy_on_write = True` vs `False`.

---

Try solving as many questions as possible using native Pandas constructors, nullable dtypes (`Int64`, `string`, `boolean`), and `.select_dtypes()` without manual Python loops.
