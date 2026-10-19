# Structured Arrays & Record Arrays Question Bank Compiled by AutoMind Team

## Beginner: Defining Structured Dtypes & Array Creation

Use this setup for Questions 1–20:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import numpy as np                                         %
%                                                            %
% # Structured data: table of employees                      %
% # Fields: name (str), age (int), salary (float)            %
%                                                            %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Define a structured data type with fields `'name'` (`U10`), `'age'` (`i4`), and `'salary'` (`f8`) using list-of-tuples format.
2. Create a structured array of 3 employees using the defined dtype and a list of tuple records.
3. Access the `'name'` column from the structured array. What is the resulting array shape and dtype?
4. Access the `'salary'` column from the structured array.
5. Access the first record (row 0) from the structured array. What type of object is returned (`np.void`)?
6. Access multiple fields simultaneously: extract both `'name'` and `'salary'` as a sub-table.
7. Modify the age of the second employee in-place.
8. Increase all salaries by 10% using vectorized arithmetic on the `'salary'` field.
9. Initialize an empty structured array of 5 records with zeros using `np.zeros(5, dtype=dtype)`.
10. Check the byte size of each record in the structured array using `.itemsize`.
11. Check the byte offset of each field in the record using `dtype.fields`.
12. Define a structured dtype using dictionary syntax: `dtype={'names': [...], 'formats': [...]}`.
13. Define a structured dtype using comma-separated format string: `dtype='U10,i4,f8'`.
14. Rename the default field names (`'f0'`, `'f1'`, `'f2'`) of an auto-named structured array.
15. Check the list of field names of a structured array using `arr.dtype.names`.
16. Create a structured array containing a boolean flag field `'is_active'` (`'?'` or `'bool'`).
17. Create a structured array containing a timestamp field `'joined_date'` with `dtype='datetime64[D]'`.
18. Check if a structured array is equal to another structured array record-by-record.
19. Convert a list of Python dictionaries to a structured array using list comprehension or mapping.
20. Check whether an array has a structured data type using `arr.dtype.names is not None`.


## Intermediate: Nested Fields, Sub-Arrays & Filtering

Use:
```python
dt = np.dtype([
    ('id', 'i4'),
    ('coords', 'f4', (3,)),        # Sub-array: 3D coordinate vector (x, y, z)
    ('score', 'f8')
])
```

21. Create a structured array where a single field contains a fixed-size 1D sub-array (3D coordinates).
22. Access the `'coords'` field and observe its shape `(N, 3)`.
23. Extract only the x-coordinate (index 0 of `'coords'`) across all records.
24. Compute the Euclidean distance of all coordinate points from the origin using `np.linalg.norm(arr['coords'], axis=1)`.
25. Define a nested structured dtype where field `'info'` is itself a structured type containing `'city'` and `'zip'`.
26. Create a record with nested fields and access the nested city: `arr['info']['city']`.
27. Filter structured array records where `'score' > 80.0` using boolean indexing.
28. Filter records where `'age' < 30` AND `'salary' >= 50000`.
29. Count how many records have `'is_active' == True`.
30. Find the record with the maximum salary using `np.argmax(arr['salary'])`.
31. Find the average salary across all employees using `np.mean(arr['salary'])`.
32. Sort a structured array in ascending order based on `'salary'` using `np.sort(arr, order='salary')`.
33. Sort a structured array based on multiple fields: first by `'age'`, then by `'salary'` using `order=['age', 'salary']`.
34. Obtain the sorting indices of a structured array based on a field using `np.argsort(arr, order='name')`.
35. Find unique records in a structured array using `np.unique()`.
36. Replace all records where `'salary' < 40000` with a minimum base salary of 40000.
37. Extract the names of all employees whose salary exceeds the mean salary.
38. Slice the first 2 records of a structured array.
39. Check if a structured array slice shares memory with the original array.
40. Copy a structured array explicitly using `.copy()`.


## Record Arrays (np.recarray) & Attribute Access

Use:
```python
struct_arr = np.array(
    [('Alice', 25, 65000.0), ('Bob', 30, 72000.0), ('Charlie', 35, 80000.0)],
    dtype=[('name', 'U10'), ('age', 'i4'), ('salary', 'f8')]
)
```

41. Convert `struct_arr` into a record array using `np.rec.array()`.
42. Convert `struct_arr` into a record array using `.view(np.recarray)`.
43. Access the `'name'` field using attribute syntax `rec_arr.name` instead of dictionary syntax `arr['name']`.
44. Access the `'salary'` field using attribute syntax `rec_arr.salary`.
45. Modify an attribute in-place using `rec_arr.age += 1`.
46. Create a record array directly using `np.rec.fromrecords()`.
47. Create a record array from a list of parallel arrays using `np.rec.fromarrays([names, ages, salaries])`.
48. Explain the difference in convenience and performance between `np.ndarray` with structured dtype and `np.recarray`.
49. Convert a record array back to a standard structured array view.
50. Check whether an object is an instance of `np.recarray`.


## Advanced: Memory Alignment, Views & Conversions

Use:
```python
unaligned_dt = np.dtype([('a', 'i1'), ('b', 'i4')])
aligned_dt = np.dtype([('a', 'i1'), ('b', 'i4')], align=True)
```

51. Check the item size of `unaligned_dt` (1 + 4 = 5 bytes).
52. Check the item size of `aligned_dt` and explain the 3 padding bytes inserted for 4-byte boundary alignment.
53. Check byte offsets of fields in `aligned_dt` using `aligned_dt.fields`.
54. Explain why aligned memory is important for C hardware memory bus performance and compiler interop.
55. Convert a 2D numeric matrix of shape `(N, 3)` into a structured array with fields `('x', 'y', 'z')` without copying memory.
56. Convert a structured array with homogeneous field types (e.g. three `f8` fields) into a standard 2D float array using `.view()`.
57. Convert a structured array to a regular 2D array using `numpy.lib.recfunctions.structured_to_unstructured()`.
58. Convert an unstructured 2D array to a structured array using `numpy.lib.recfunctions.unstructured_to_structured()`.
59. Add a new field `'bonus'` (`f8`) to an existing structured array using `numpy.lib.recfunctions.append_fields()`.
60. Drop a field from a structured array using `numpy.lib.recfunctions.drop_fields()`.
61. Rename a field in a structured array using `numpy.lib.recfunctions.rename_fields()`.
62. Merge two structured arrays column-wise using `numpy.lib.recfunctions.merge_arrays()`.
63. Join two structured arrays on a common key field (database-style inner join) using `numpy.lib.recfunctions.join_by()`.
64. Stack two structured arrays with identical fields row-wise using `np.concatenate()`.
65. Save a structured array to a binary `.npy` file and verify all field definitions are preserved upon reload.
66. Save a structured array to a CSV file using `np.savetxt()` with custom format specifiers.
67. Load a CSV with mixed string and numeric columns into a structured array using `np.genfromtxt(names=True, dtype=None)`.
68. Create a structured array from a raw binary buffer using `np.frombuffer()`.
69. Pack a structured array into raw bytes using `.tobytes()`.
70. Inspect the byte representation of an aligned record to see padding bytes.


## Multi-Dimensional Structured Arrays & Tables

Use:
```python
grid_dt = np.dtype([
    ('elevation', 'f4'),
    ('temperature', 'f4'),
    ('land_cover', 'i2')
])
```

71. Create a 2D spatial grid of shape `(100, 100)` where each cell is a structured record with elevation and temperature.
72. Access the `'elevation'` layer of the 2D grid to obtain a standard 2D float array of shape `(100, 100)`.
73. Compute the mean temperature across the entire 2D spatial grid.
74. Find coordinates `(row, col)` of the cell with the highest elevation using `np.unravel_index(np.argmax(grid['elevation']))`.
75. Create a 3D volume of structured voxels representing density and pressure.
76. Apply a 2D boolean condition: find grid cells where `elevation > 500` AND `temperature < 0`.
77. Update elevation values for a slice of the 2D grid in-place.
78. Initialize a 2D grid of structured records with zeros using `np.zeros((50, 50), dtype=grid_dt)`.
79. Compute gradient of elevation across the grid using `np.gradient(grid['elevation'])`.
80. Save the multi-layer spatial grid to a compressed `.npz` file.


## Challenge Questions: Relational Operations & C-Struct Interop

81. **C-Struct Binary Parsing**: Parse a binary packet stream originating from a C struct `typedef struct { uint32_t id; float val; char tag[8]; } Packet;` using an aligned structured dtype.
82. **SQL Group By & Aggregation**: Perform a GROUP BY operation on a structured array of sales records (group by `'store_id'` and compute total `'revenue'`) using `np.unique()` and `np.bincount()`.
83. **Outer Join on Structured Tables**: Implement an outer join of two structured arrays on a shared ID key without external libraries.
84. **Pandas DataFrame Zero-Copy Interop**: Convert a structured NumPy array into a Pandas DataFrame without copying data buffers.
85. **Fast Columnar Sorting**: Sort a 1,000,000-record structured array by primary key `'category'` and secondary key `'timestamp'` using `np.lexsort()`.
86. **Variable-Length Strings in Structured Arrays**: Explain why standard structured arrays require fixed-length strings (`'U10'`) and how object arrays (`'O'`) can store variable strings.
87. **Heterogeneous Masked Array**: Create a masked structured array using `np.ma.array` to mask invalid records.
88. **Bitfield Record Definition**: Simulate a bitfield packed struct using unsigned integer bitwise operations on a structured array field.
89. **Memory Mapping Huge Structured Files**: Memory map a 10 GB binary telemetry file into a structured array using `np.memmap()` for instant indexed access.
90. **Mesh Vertex/Face Topology Table**: Define a 3D geometry mesh representation using two structured arrays: `vertices` (`x, y, z`) and `faces` (indices `v0, v1, v2`).
91. **Data Normalization by Column**: Normalize all numeric fields of a structured array to $[0, 1]$ while leaving categorical/string fields untouched.
92. **Dtype Migration**: Safely cast a structured array to a new dtype where one column's precision is promoted from `float32` to `float64`.
93. **Sub-Array Matrix Inversion**: Given a structured array where each record contains a 3×3 matrix field `'transform'`, invert all matrices in a vectorized manner using `np.linalg.inv()`.
94. **Point Cloud KD-Tree Preparation**: Reorder a structured point cloud array `('x', 'y', 'z', 'intensity')` along a Morton spatial code (Z-order curve).
95. **Duplicate Record Detection**: Find and remove all duplicate rows across all fields in a structured dataset.
96. **Filtering by String Prefix**: Filter records where string field `'country'` starts with `'United'` using `np.char.startswith()`.
97. **Endianness Conversion for Network Packets**: Swap byte ordering of all fields in a structured network packet array from network byte order (big-endian) to host byte order.
98. **Structured Array to JSON**: Serialize a structured array into a JSON string of records.
99. **Columnar vs Row-Oriented Storage**: Compare the memory layout and cache performance of a single structured array of records vs a dictionary of separate 1D arrays.
100. **Recfunctions Fast Concatenation**: Safely concatenate two structured arrays that have slightly differing field orders using `numpy.lib.recfunctions.stack_arrays()`.

---

Try solving as many questions as possible using NumPy structured arrays, record arrays (`np.recarray`), and `numpy.lib.recfunctions` utilities without using Python `for` loops.
