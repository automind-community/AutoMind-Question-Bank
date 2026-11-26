# File I/O & Serialization Question Bank Compiled by AutoMind Team

## Beginner: CSV & Delimited Text Files

Use this setup for Questions 1–15:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import pandas as pd                                        %
% import io                                                  %
%                                                            %
% df = pd.DataFrame({                                        %
%     'id': [1, 2, 3],                                       %
%     'name': ['Alice', 'Bob', 'Charlie'],                   %
%     'score': [91.5, 84.0, 77.5],                           %
%     'joined': ['2026-01-01', '2026-02-15', '2026-03-10']   %
% })                                                         %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Save `df` to a CSV file `'students.csv'` without writing the DataFrame index (`index=False`).
2. Read `'students.csv'` back into a DataFrame using `pd.read_csv('students.csv')`.
3. Read only specific columns `['name', 'score']` from `'students.csv'` using `usecols`.
4. Read only the first 2 rows of `'students.csv'` using `nrows=2`.
5. Skip the first 2 data rows when reading a CSV using `skiprows=[1, 2]`.
6. Parse `'joined'` directly as `datetime64[ns]` during `pd.read_csv()` using `parse_dates=['joined']`.
7. Enforce explicit column data types during CSV loading using `dtype={'id': 'int32', 'score': 'float32'}`.
8. Treat custom sentinel strings `['NA', 'N/A', 'missing', '-']` as `NaN` during `pd.read_csv()` using `na_values`.
9. Read a tab-separated file (`.tsv`) using `sep='\t'` and a semicolon-separated file using `sep=';'`.
10. Read a CSV file that has no header row (`header=None`) and assign custom column names with `names=['id', 'name', 'score', 'joined']`.
11. Save `df` directly to a gzip-compressed CSV `'students.csv.gz'` using `compression='gzip'`.
12. Read `'students.csv'` using `dtype_backend='pyarrow'` (or `'numpy_nullable'`) for nullable dtypes.
13. Read a CSV from an in-memory string buffer `io.StringIO(csv_text)` instead of a disk file.
14. Export `df` to a CSV string in memory by calling `df.to_csv(index=False)` with no path argument.
15. Handle quoted fields containing commas and custom thousands separators (`thousands=','`, `decimal='.'`) in `pd.read_csv()`.


## Intermediate: JSON, HTML, XML & Clipboard

Use:
```python
json_str = '[{"id": 1, "user": {"name": "Alice", "city": "NYC"}}, {"id": 2, "user": {"name": "Bob", "city": "LA"}}]'
```

16. Load a JSON string or file into a DataFrame using `pd.read_json(io.StringIO(json_str))`.
17. Export `df` to JSON in record-oriented format (`orient='records'`) and line-delimited JSON (`orient='records', lines=True`).
18. Read a newline-delimited JSON (`.jsonl` / NDJSON) file using `pd.read_json(..., lines=True)`.
19. Flatten nested JSON objects (`json_str` above) into flat columns `'id'`, `'user.name'`, `'user.city'` using `pd.json_normalize()`.
20. Use `pd.json_normalize()` with `record_path` and `meta` to flatten a list of nested sub-records while keeping parent fields.
21. Extract all `<table>` elements from an HTML page or HTML string into a list of DataFrames using `pd.read_html()`.
22. Export `df` to a clean HTML table without index using `df.to_html(index=False)`.
23. Read an XML file or string into a DataFrame using `pd.read_xml()` and export with `df.to_xml()`.
24. Export `df` to Markdown table format using `df.to_markdown(index=False)`.
25. Read tabular data copied to the system clipboard using `pd.read_clipboard()` and copy `df` to clipboard using `df.to_clipboard(index=False)`.


## Excel Workbooks (.xlsx)

26. Save `df` to an Excel file `'report.xlsx'` on sheet `'Summary'` without the index using `df.to_excel()`.
27. Read sheet `'Summary'` from `'report.xlsx'` using `pd.read_excel('report.xlsx', sheet_name='Summary')`.
28. Read **all sheets** of an Excel workbook into a dictionary of DataFrames using `sheet_name=None`.
29. Write multiple DataFrames (`df1`, `df2`) to different sheets of the same `'multi_report.xlsx'` file using `with pd.ExcelWriter(...) as writer:`.
30. Append a new sheet to an existing `.xlsx` file using `pd.ExcelWriter(..., mode='a', if_sheet_exists='replace')`.


## Binary & Columnar Formats (Parquet, Feather, Pickle, HDF5)

31. Save `df` to a Parquet file `'data.parquet'` using `df.to_parquet()` and read it back with `pd.read_parquet()`.
32. Read only specific columns `['name', 'score']` from `'data.parquet'` using `columns=['name', 'score']` (column projection pushdown).
33. Save `df` to Parquet partitioned by `'joined'` (or `'category'`) into a directory hierarchy using `partition_cols=['category']`.
34. Save `df` to Apache Arrow Feather format (`'data.feather'`) using `df.to_feather()` and read it back with `pd.read_feather()`.
35. Serialize a `DataFrame` to a Python pickle file `'data.pkl'` using `df.to_pickle()` and load it with `pd.read_pickle()`.
36. Compare file sizes and read/write speeds of CSV vs Parquet vs Feather for a 100,000-row DataFrame.
37. Explain why Parquet is preferred over Pickle for long-term storage and cross-language interoperability.
38. Save multiple DataFrames into a single HDF5 store using `with pd.HDFStore('store.h5') as store:` and query them.
39. Write a `DataFrame` to an in-memory `io.BytesIO()` buffer in Parquet format and read it back.
40. Specify Snappy vs Zstandard compression in `df.to_parquet('data.parquet', compression='zstd')`.


## SQL Databases & Chunked Streaming

41. Connect to an in-memory SQLite database (`sqlite3.connect(':memory:')`) and write `df` to a table `'students'` using `df.to_sql('students', conn, if_exists='replace', index=False)`.
42. Read an entire SQL table `'students'` using `pd.read_sql_table()` (with SQLAlchemy) or `pd.read_sql('SELECT * FROM students', conn)`.
43. Execute a parameterized SQL query using `pd.read_sql_query('SELECT * FROM students WHERE score > ?', conn, params=(80,))`.
44. Stream a large SQL query in chunks of 1,000 rows using `pd.read_sql_query(..., chunksize=1000)`.
45. Read a huge CSV file in chunks of 10,000 rows using `pd.read_csv(..., chunksize=10000)` and iterate over the `TextFileReader`.


## Challenge Questions: Production I/O Pipelines

46. **Out-of-Core Chunked Aggregation**: Compute the total sum of `'amount'` grouped by `'category'` from a 10M-row CSV using `chunksize=100_000` without loading the entire file into memory.
47. **Multi-File Glob Ingestion**: Read and concatenate all `sales_*.csv` files in a directory while adding a `'source_file'` column recording which file each row came from.
48. **Encoding & Bad-Line Recovery**: Safely read a legacy CSV encoded in `'latin-1'` containing malformed lines using `encoding='latin-1'` and `on_bad_lines='skip'`.
49. **Schema-Validated Parquet Export**: Before writing to Parquet, cast all columns to explicit target dtypes, verify zero `object` columns remain, and write with `index=False`.
50. **Incremental SQLite Upsert / Append**: Read a CSV in chunks and append each chunk into an SQLite table using `to_sql(..., if_exists='append', method='multi')`.

---

Try solving as many questions as possible using Pandas' native I/O readers/writers (`read_csv`, `read_parquet`, `read_json`, `json_normalize`, `read_excel`, `read_sql_query`) and `chunksize` streaming.
