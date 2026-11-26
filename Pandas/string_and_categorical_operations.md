# String & Categorical Operations Question Bank Compiled by AutoMind Team

## Beginner: Basic .str Accessor Operations

Use this setup for Questions 1–10:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import pandas as pd                                        %
% import numpy as np                                         %
%                                                            %
% names = pd.Series([                                        %
%     '  alice smith ', 'BOB JONES', 'Charlie Brown',        %
%     'diana_prince', np.nan, '  Evan-Lee  '                 %
% ])                                                         %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Convert all strings in `names` to lowercase using `.str.lower()`.
2. Convert all strings in `names` to uppercase using `.str.upper()` and title case using `.str.title()`.
3. Remove leading and trailing whitespace from `names` using `.str.strip()`.
4. Compute the character length of each string using `.str.len()`.
5. Replace underscores `'_'` and hyphens `'-'` with spaces using `.str.replace()`.
6. Check which entries contain `'alice'` (case-insensitive) using `.str.contains('alice', case=False, na=False)`.
7. Check which entries start with `'B'` or `'C'` (after stripping whitespace) using `.str.startswith()`.
8. Check which entries end with `'Brown'` using `.str.endswith()`.
9. Slice the first 3 characters of each string using `.str.slice(0, 3)` (or `.str[:3]`).
10. Concatenate all non-null strings in `names` into a single comma-separated string using `.str.cat(sep=', ')`.


## Intermediate: Splitting, Regex Extraction & Formatting

Use:
```python
logs = pd.Series([
    '2026-05-01 | INFO | user=101 | action=login',
    '2026-05-01 | ERROR | user=204 | action=timeout',
    '2026-05-02 | WARN | user=101 | action=retry',
    '2026-05-02 | INFO | user=309 | action=logout'
])
```

11. Split each log line on `' | '` into a `Series` of lists using `.str.split(' | ', regex=False)`.
12. Split each log line on `' | '` directly into separate `DataFrame` columns using `expand=True`.
13. Split each log line only on the first `' | '` (`n=1, expand=True`).
14. Extract the log level (`INFO`, `ERROR`, `WARN`) using `.str.extract(r'\|\s*(\w+)\s*\|')`.
15. Extract both `user` ID and `action` into named DataFrame columns `['user_id', 'action']` using named regex capture groups `(?P<user_id>...)` in `.str.extract()`.
16. Find all key-value pairs `key=val` in each line using `.str.findall(r'(\w+)=(\w+)')`.
17. Extract all matches across multiple rows into a MultiIndexed DataFrame using `.str.extractall()`.
18. Count how many times the letter `'o'` appears in each log line using `.str.count('o')`.
19. Check whether each string in a `Series` `pd.Series(['123', '45a', '678'])` consists purely of digits using `.str.isdigit()`.
20. Pad numeric IDs `pd.Series(['7', '42', '105'])` with leading zeros to width 5 using `.str.zfill(5)`.
21. Left-justify and center-align strings to width 12 using `.str.ljust(12, '.')` and `.str.center(12, '-')`.
22. Normalize Unicode characters (e.g., `'café'` -> `'cafe'`) using `.str.normalize('NFKD')`.
23. Concatenate two string columns `df['first']` and `df['last']` with a space separator using `.str.cat(df['last'], sep=' ')`.
24. Replace matched regex groups dynamically using `.str.replace()` with a callable function.
25. Split a multi-label tag column `'python|pandas|sql'` into one-hot encoded dummy columns using `.str.get_dummies(sep='|')`.


## Categorical Data: Creation, Ordering & Manipulation

Use this DataFrame for Questions 26–40:

```python
survey = pd.DataFrame({
    'respondent': ['R1', 'R2', 'R3', 'R4', 'R5', 'R6'],
    'satisfaction': ['Low', 'High', 'Medium', 'Low', 'Very High', 'Medium'],
    'age_group': ['18-25', '26-35', '36-50', '18-25', '50+', '26-35']
})
```

26. Convert `'satisfaction'` to an unordered `category` dtype using `.astype('category')`.
27. Create an ordered `pd.Categorical` for `'satisfaction'` with explicit order `['Low', 'Medium', 'High', 'Very High']` (`ordered=True`).
28. Inspect the categories and underlying integer codes using `.cat.categories` and `.cat.codes`.
29. Sort `survey` by `'satisfaction'` and observe how ordered categories sort logically rather than alphabetically.
30. Filter `survey` for respondents with `'satisfaction' >= 'Medium'` using ordered categorical comparison.
31. Rename categories using `.cat.rename_categories({'Low': 'Poor', 'Medium': 'Fair', 'High': 'Good', 'Very High': 'Excellent'})`.
32. Add a new unused category `'Neutral'` using `.cat.add_categories(['Neutral'])`.
33. Remove any unused categories from the `Categorical` using `.cat.remove_unused_categories()`.
34. Reorder the categories of `'age_group'` to `['18-25', '26-35', '36-50', '50+']` with `ordered=True` using `.cat.reorder_categories()`.
35. Set all values in `'satisfaction'` to unordered using `.cat.as_unordered()`.
36. Compare memory usage of a 100,000-row string column with 5 unique values stored as `object` vs `category`.
37. Explain what happens when you assign a value not present in `.cat.categories` to a categorical `Series`.
38. Use `pd.cut()` to bin continuous ages `[19, 27, 44, 62, 31]` into ordered categorical bins `[18, 25, 35, 50, 100]`.
39. Use `pd.qcut()` to split a numeric `Series` into 4 equal-frequency (quartile) categorical bins.
40. Perform a `groupby('satisfaction', observed=False)` on a categorical column and explain the `observed` parameter.


## Advanced String & Categorical Patterns

41. Convert a `Series` of strings to Pandas' nullable `string[pyarrow]` or `'string'` dtype and test `.str.upper()` with `pd.NA`.
42. Extract domain names from an email `Series` `['alice@gmail.com', 'bob@company.org', 'eve@uni.edu']` using `.str.split('@').str[1]`.
43. Filter a `DataFrame` where a `'skills'` column contains both `'Python'` and `'SQL'` (in any order) using regex lookaheads in `.str.contains()`.
44. Use `.str.fullmatch()` vs `.str.match()` to validate exact postal codes (e.g., `^\d{5}$`).
45. Convert a categorical column back to regular strings using `.astype('string')` or `.astype(str)`.


## Challenge Questions: Text Parsing & Categorical Pipelines

46. **Email & Username Parser**: Given `['John Doe <jdoe@example.com>', 'Jane <jane@test.org>']`, extract `full_name`, `username`, and `domain` into three separate DataFrame columns using a single `.str.extract()` call.
47. **Categorical Encoding for ML**: Encode an ordered `'size'` column (`S < M < L < XL`) into numeric codes while preserving `NaN` as `-1` (and converting `-1` back to `np.nan` if needed).
48. **Multi-Value Tag Frequency**: Given a column of comma-separated tags `['a,b', 'b,c', 'a,c,d']`, compute the frequency of each individual tag using `.str.split(',').explode().value_counts()`.
49. **Slug Generator**: Transform messy article titles `['  Hello, World! (2026) ', 'Pandas 2.0: Tips & Tricks!']` into URL-safe lowercase slugs (`'hello-world-2026'`, `'pandas-2-0-tips-tricks'`) using chained `.str` methods.
50. **Top-N Categories + 'Other'**: Given a high-cardinality categorical column, keep only the top 5 most frequent categories and collapse all remaining categories into `'Other'`.

---

Try solving as many questions as possible using Pandas `.str` and `.cat` accessors, `pd.cut()`, and `pd.qcut()` without Python `for` loops.
