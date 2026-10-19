# File I/O & Serialization Question Bank Compiled by AutoMind Team

## Beginner: Saving & Loading Binary .npy Files

Use this setup for Questions 1–20:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import numpy as np                                         %
%                                                            %
% arr = np.arange(10, dtype=np.int32)                        %
% mat = np.random.default_rng(42).normal(size=(5, 5))         %
%                                                            %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Save array `arr` to a binary file named `'my_array.npy'` using `np.save()`.
2. Load the binary file `'my_array.npy'` back into memory using `np.load()`.
3. Check if the loaded array is identical to `arr` in values and data type.
4. Save matrix `mat` to `'matrix.npy'` using `np.save()`.
5. What metadata is stored inside a `.npy` header file (magic string, version, shape, dtype, Fortran order)?
6. Open and inspect the first few bytes of a `.npy` file in binary read mode (`'rb'`).
7. Save an array to an open file-like buffer (e.g. `io.BytesIO()`) instead of a disk file.
8. Load an array from an in-memory `io.BytesIO` buffer using `np.load()`.
9. Save an array of strings to a `.npy` file and verify string retention upon loading.
10. Save a structured array to `.npy` and check if column field names and types are preserved.
11. Save a boolean array to `.npy` and verify its integrity.
12. Save an array containing `np.nan` and `np.inf` values and verify they load accurately.
13. Overwrite an existing `.npy` file by saving with the same filename.
14. Load a `.npy` file with `allow_pickle=False` for secure execution.
15. What security vulnerability exists when loading `.npy` files with `allow_pickle=True` from untrusted sources?
16. Save a 3D tensor of shape `(2, 3, 4)` to a `.npy` file.
17. Verify that shape and dimensionality are restored upon loading.
18. Check the file size on disk of `'my_array.npy'` using `os.path.getsize()`.
19. Save an array with `float32` vs `float64` and compare the resulting file sizes on disk.
20. Save an array without explicitly typing `.npy` in the filename and verify that NumPy automatically appends the extension.


## Intermediate: Compressed Archives (.npz) & Multi-Array Storage

Use:
```python
x = np.linspace(0, 10, 100)
y = np.sin(x)
weights = np.ones((10, 10))
```

21. Save multiple arrays `x`, `y`, and `weights` into a single uncompressed archive `'data.npz'` using `np.savez()`.
22. Save multiple arrays with custom named keyword arguments: `np.savez('named_data.npz', x_vals=x, y_vals=y, w=weights)`.
23. Load `'named_data.npz'` using `np.load()` and store the returned object in `archive`.
24. List all array names stored inside `archive` using `archive.files`.
25. Access and extract array `x_vals` from `archive` using dictionary key syntax `archive['x_vals']`.
26. Close the loaded `NpzFile` archive using `archive.close()` or a context manager (`with np.load(...) as f:`).
27. Save multiple arrays into a compressed archive `'data_compressed.npz'` using `np.savez_compressed()`.
28. Compare the disk file size between uncompressed `'data.npz'` and compressed `'data_compressed.npz'`.
29. Save a large array of zeros to both `.npz` and `.npz` compressed to observe the compression ratio.
30. Load an array from a compressed archive and verify it matches the original uncompressed array.
31. Update an existing `.npz` file by adding a new array (reading existing arrays and re-saving).
32. Delete temporary `.npy` and `.npz` files using Python's `os.remove()`.
33. Check whether `archive` loads all arrays eagerly into memory or lazily on demand.
34. Check the dtype and shape of an array inside an `NpzFile` without loading other arrays in the archive.
35. Iterate over all array names in an `NpzFile` and print their shapes.
36. Save a dictionary of arrays `{'arr1': x, 'arr2': y}` into an `.npz` archive using keyword argument unpacking `**dict`.
37. Save a machine learning model's weights and biases into a single `.npz` checkpoint file.
38. Load and restore weight tensors from a model checkpoint archive.
39. Check if `.npz` files can be opened using standard zip extraction tools (e.g. Python's `zipfile` module).
40. Inspect the file list of an `.npz` file using Python's `zipfile.ZipFile()`.


## Text Files (CSV, TXT, TSV): loadtxt, savetxt & genfromtxt

Use:
```python
data = np.array([
    [1.0, 2.5, 3.8],
    [4.2, 5.0, 6.1],
    [7.9, 8.3, 9.4]
])
```

41. Save matrix `data` to a comma-separated text file `'data.csv'` using `np.savetxt()` with `delimiter=','`.
42. Save `data` to a tab-separated text file `'data.tsv'` with `delimiter='\\t'`.
43. Format output numbers with 2 decimal places using `fmt='%.2f'` in `np.savetxt()`.
44. Save an integer array to a text file using integer formatting `fmt='%d'`.
45. Add a header line `'col1,col2,col3'` to a CSV file using `header='col1,col2,col3'`.
46. Add a footer line to a text file using `footer='End of file'`.
47. Suppress the default `# ` comment prefix on headers by setting `comments=''`.
48. Load `'data.csv'` back into a NumPy array using `np.loadtxt(..., delimiter=',')`.
49. Load only columns 0 and 2 from `'data.csv'` using `usecols=(0, 2)`.
50. Skip the first header row when loading a CSV file using `skiprows=1`.
51. Load data into a specific data type using `dtype=float` in `np.loadtxt()`.
52. Given a CSV file with missing values, load it using `np.genfromtxt(..., delimiter=',')`.
53. Fill missing values with -999.0 using `filling_values=-999.0` in `np.genfromtxt()`.
54. Automatically detect header names as structured array fields using `names=True` in `np.genfromtxt()`.
55. Load a CSV containing dates, strings, and numbers into a structured array using `dtype=None` and `encoding='utf-8'`.
56. Use custom converters in `np.loadtxt()` to parse percentage strings (e.g., `'75%'`) into floats (`0.75`).
57. Compare execution time between loading a 100,000-row array from `.npy` vs `.csv`.
58. Explain why binary `.npy` format is much faster and smaller than plain text CSV.
59. Save a 1D array to a text file with each element on a new line.
60. Save a 1D array to a text file with space-separated values on a single line.


## Raw Binary Files: tofile & fromfile

Use:
```python
raw_arr = np.arange(16, dtype=np.int32).reshape(4, 4)
```

61. Write `raw_arr` to a raw binary file `'raw_data.bin'` using `raw_arr.tofile()`.
62. Read `'raw_data.bin'` back using `np.fromfile('raw_data.bin', dtype=np.int32)`.
63. Explain why `np.fromfile()` loads data as a flat 1D array regardless of the original shape.
64. Reshape the array loaded via `np.fromfile()` back to its original shape `(4, 4)`.
65. Explain why `tofile()` and `fromfile()` do NOT preserve array shape, dtype, or endianness metadata.
66. Read only the first 8 elements from `'raw_data.bin'` using `count=8` in `np.fromfile()`.
67. Read binary data starting from a specific byte offset using Python's file `seek()`.
68. Convert `raw_arr` directly into a Python `bytes` object using `raw_arr.tobytes()`.
69. Reconstruct an array from a Python `bytes` object using `np.frombuffer()`.
70. Write an array directly to an open binary file descriptor using `tofile()`.


## Memory-Mapped Files (np.memmap) for Big Data

Use:
```python
filename = 'large_array.dat'
shape = (1000, 1000)
dtype = np.float32
```

71. Create a memory-mapped array of shape `(1000, 1000)` on disk in write mode using `np.memmap(filename, dtype=dtype, mode='w+', shape=shape)`.
72. Write data to a slice of the memory-mapped array without loading the full array into RAM.
73. Flush in-memory modifications to disk using `mmap_arr.flush()`.
74. Open an existing memory-mapped file in read-only mode using `mode='r'`.
75. Open an existing memory-mapped file in copy-on-write mode using `mode='c'`.
76. Explain why `mode='c'` allows modifying array data in memory without altering the underlying file on disk.
77. Read a single row from a multi-gigabyte memory-mapped file and verify minimal RAM usage.
78. Access a sub-matrix from a memory-mapped array and check whether it returns a memory view.
79. Create a memory-mapped array starting from a non-zero byte offset in an existing file using parameter `offset=...`.
80. Safely close and delete a memory-mapped file by deleting references (`del mmap_arr`) and calling `os.remove()`.


## 3D & Tensor Serialization

Use:
```python
images = np.random.default_rng(42).integers(0, 256, size=(100, 28, 28, 3), dtype=np.uint8)
```

81. Save a 4D image dataset of shape `(100, 28, 28, 3)` to a `.npy` file.
82. Load only a subset (e.g. the first 10 images) from a `.npy` file using `mmap_mode='r'` without reading all 100 images into memory.
83. Explain how `mmap_mode='r'` in `np.load('file.npy', mmap_mode='r')` enables out-of-core data processing.
84. Measure the load time difference between `np.load('file.npy')` and `np.load('file.npy', mmap_mode='r')`.
85. Save multiple tensor batches into a `.npz` archive.
86. Save training images and ground-truth labels into `'dataset.npz'`.
87. Extract image batches iteratively from `'dataset.npz'` in a training loop.
88. Save a 3D tensor to disk as raw binary and reconstruct it with `.fromfile().reshape()`.
89. Save float tensors in half-precision `float16` to reduce disk footprint by 50% compared to `float32`.
90. Verify that loading half-precision tensors maintains numerical validity.


## Challenge Questions: Advanced I/O Pipelines & Interoperability

91. **Streaming Batch Processor**: Implement a generator function that streams batches of data from a large `.npy` file using `mmap_mode='r'` without exhausting system memory.
92. **HDF5 / Zarr Comparison**: Discuss how NumPy I/O compares with HDF5 (`h5py`) and Zarr for chunked multi-dimensional array storage.
93. **Custom Binary Protocol**: Design a binary file format consisting of a 16-byte custom header (magic number, dimensions, dtype code) followed by raw array buffer data.
94. **Fast CSV Parsing via Memoryview**: Parse a multi-column numerical CSV file into a NumPy array using chunked binary reading.
95. **In-Memory Pipe Serialization**: Serialize an array to bytes, send it over a simulated network socket, and deserialize it on the receiver using `np.load(io.BytesIO(data))`.
96. **Safe Model Checkpoint Restoration**: Write a function that safely validates and loads model tensor weights from an `.npz` archive without allowing malicious code execution.
97. **Chunked Array Aggregation**: Compute the global mean and variance of a dataset stored across 10 separate `.npy` files without loading more than one file into RAM at a time.
98. **Memory-Mapped Sliding Window**: Compute a sliding window feature matrix over a multi-gigabyte continuous sensor recording using `np.memmap()`.
99. **Zero-Copy File Descriptor Passing**: Memory-map a file using Python's `mmap.mmap` and create an ndarray view on top of it.
100. **NPY Format Header Inspection**: Parse the shape and dtype of a `.npy` file directly from its ASCII header string without loading the array data buffer.

---

Try solving as many questions as possible using NumPy's file I/O tools (`save`, `load`, `savez`, `savez_compressed`, `savetxt`, `loadtxt`, `genfromtxt`, `memmap`) without using Python `for` loops.
