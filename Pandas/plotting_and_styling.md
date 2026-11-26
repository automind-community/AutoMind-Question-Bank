# Plotting & Styling Question Bank Compiled by AutoMind Team

## Beginner: Built-in DataFrame & Series Plotting (.plot)

Use this setup for Questions 1–10:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import pandas as pd                                        %
% import numpy as np                                         %
%                                                            %
% df = pd.DataFrame({                                        %
%     'month': ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'],   %
%     'revenue': [120, 145, 132, 168, 190, 210],             %
%     'cost': [80, 90, 85, 100, 110, 115],                   %
%     'profit': [40, 55, 47, 68, 80, 95]                     %
% }).set_index('month')                                      %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Create a line plot of all numeric columns in `df` using `df.plot()`.
2. Create a line plot of only `'revenue'` and `'profit'` with a title `'Monthly Financials'` and gridlines (`grid=True`).
3. Create a vertical bar chart of `'revenue'` using `df['revenue'].plot(kind='bar')`.
4. Create a horizontal bar chart comparing `'revenue'` and `'cost'` using `df[['revenue', 'cost']].plot.barh()`.
5. Create a stacked bar chart of `'cost'` and `'profit'` using `stacked=True`.
6. Create an area plot of `'cost'` and `'profit'` with transparency `alpha=0.5` using `df[['cost', 'profit']].plot.area()`.
7. Plot each column in its own separate subplot stacked vertically using `df.plot(subplots=True, figsize=(8, 6))`.
8. Plot `'revenue'` on the primary y-axis and `'profit'` on a secondary y-axis using `secondary_y=['profit']`.
9. Save a Pandas plot directly to a PNG file `'chart.png'` by capturing the returned `Axes` object (`ax.get_figure().savefig(...)`).
10. Customize line styles, colors, and markers in `df.plot(style=['-o', '--s', ':^'])`.


## Intermediate: Statistical Plots (Hist, Box, Scatter, Pie, KDE)

Use:
```python
rng = np.random.default_rng(42)
iris_like = pd.DataFrame({
    'sepal_len': rng.normal(5.8, 0.8, 150),
    'sepal_wid': rng.normal(3.0, 0.4, 150),
    'petal_len': rng.normal(3.8, 1.7, 150),
    'species': rng.choice(['setosa', 'versicolor', 'virginica'], size=150)
})
```

11. Create a histogram of `'sepal_len'` with 20 bins using `iris_like['sepal_len'].plot.hist(bins=20)`.
12. Plot overlapping histograms for all numeric columns using `iris_like.plot.hist(alpha=0.5, bins=25)`.
13. Create a Kernel Density Estimate (KDE) plot of `'petal_len'` using `.plot.kde()`.
14. Create a box plot comparing all numeric columns using `iris_like.plot.box()`.
15. Create grouped box plots of `'sepal_len'` split by `'species'` using `iris_like.boxplot(column='sepal_len', by='species')`.
16. Create a scatter plot of `'sepal_len'` vs `'petal_len'` using `iris_like.plot.scatter(x='sepal_len', y='petal_len')`.
17. Color scatter plot points by `'sepal_wid'` using `c='sepal_wid', colormap='viridis'`.
18. Scale scatter plot point sizes by a numeric column using `s=iris_like['petal_len'] * 15`.
19. Create a 2D hexagonal bin plot for dense scatter data using `.plot.hexbin(x='sepal_len', y='petal_len', gridsize=20)`.
20. Create a pie chart of `'species'` counts with percentage labels (`autopct='%.1f%%'`) using `iris_like['species'].value_counts().plot.pie()`.


## Specialized Pandas Plotting Utilities (pd.plotting)

21. Create a scatter matrix (pairplot) of all numeric columns with diagonal KDEs using `pd.plotting.scatter_matrix(iris_like, diagonal='kde')`.
22. Create a lag plot (`lag=1`) for a time series `s` to check autocorrelation using `pd.plotting.lag_plot(s)`.
23. Create an autocorrelation plot across lags using `pd.plotting.autocorrelation_plot(s)`.
24. Plot multivariate parallel coordinates grouped by `'species'` using `pd.plotting.parallel_coordinates(iris_like, 'species')`.
25. Plot Andrews curves for multivariate cluster visualization using `pd.plotting.andrews_curves(iris_like, 'species')`.


## DataFrame Styling (df.style)

Use this summary DataFrame for Questions 26–45:

```python
perf = pd.DataFrame({
    'team': ['Alpha', 'Beta', 'Gamma', 'Delta'],
    'revenue': [450000.5, 310000.0, 520000.75, 195000.25],
    'growth': [0.145, -0.032, 0.228, 0.051],
    'margin': [0.31, 0.24, 0.38, np.nan]
})
```

26. Format `'revenue'` as `'$450,000.50'` and `'growth'`/`'margin'` as percentages `'14.5%'` using `perf.style.format()`.
27. Replace `NaN` display text in styled output with `'—'` using `.format(na_rep='—')`.
28. Highlight the maximum value in each numeric column in light green using `.highlight_max(color='lightgreen')`.
29. Highlight the minimum value in each numeric column in light coral using `.highlight_min(color='lightcoral')`.
30. Highlight missing (`NaN`) cells in yellow using `.highlight_null(color='yellow')`.
31. Highlight values in `'growth'` between `0.0` and `0.15` using `.highlight_between(subset=['growth'], left=0.0, right=0.15)`.
32. Apply a continuous color heatmap across `'revenue'` using `.background_gradient(subset=['revenue'], cmap='YlGnBu')`.
33. Apply a text color gradient across `'margin'` using `.text_gradient(subset=['margin'], cmap='RdYlGn')`.
34. Render horizontal data bars inside `'revenue'` cells using `.bar(subset=['revenue'], color='#5fba7d')`.
35. Render diverging bars (red for negative, green for positive) on `'growth'` using `.bar(subset=['growth'], align='mid', color=['#d65f5f', '#5fba7d'])`.
36. Hide the DataFrame row index in the styled output using `.hide(axis='index')`.
37. Add a table title caption `'Q1 Team Performance'` using `.set_caption('Q1 Team Performance')`.
38. Apply custom CSS properties (e.g., `{'font-weight': 'bold', 'text-align': 'center'}`) to `'team'` using `.set_properties()`.
39. Apply a custom conditional styling function (red text if `< 0` else black) across `'growth'` using `perf.style.map(..., subset=['growth'])`.
40. Highlight an entire row if `'growth' < 0` using `perf.style.apply(..., axis=1)`.
41. Set hover/table-wide CSS styles (e.g., alternating row striping or hover highlight) using `.set_table_styles([...])`.
42. Export a styled `Styler` object to an HTML string using `.to_html()`.
43. Export a styled `Styler` object to an Excel file preserving colors and formatting using `.to_excel('styled.xlsx', engine='openpyxl', index=False)`.
44. Export a styled `Styler` object to LaTeX table code using `.to_latex()`.
45. Chain multiple `.style` operations (format + gradient + bar + caption + hide index) in a single expression.


## Challenge Questions: Executive Dashboards & Custom Visuals

46. **Plotly / Interactive Plotting Backend**: Switch Pandas' plotting backend to `'plotly'` (if installed) via `pd.options.plotting.backend = 'plotly'` and generate an interactive line chart.
47. **Quantile-Colored Styler**: Write a `.style.apply()` function that colors the top 25% of each numeric column green and bottom 25% red dynamically.
48. **Dual-Metric Annotated Chart**: Plot `'revenue'` as bars and `'growth'` as a line on a secondary y-axis with custom axis labels and legend placement.
49. **Heatmap Correlation Matrix**: Compute `df.corr()` and render it as a publication-ready annotated heatmap table using `.style.background_gradient(cmap='coolwarm', vmin=-1, vmax=1).format('{:.2f}')`.
50. **Sparkline / Bar-Table Report**: Build a styled summary table combining `groupby` metrics (`sum`, `mean`, `count`) with formatted currencies, inline bars, and hidden index ready for HTML email export.

---

Try solving as many questions as possible using `df.plot()`, `pd.plotting`, and `df.style` method chaining without manual Matplotlib loops where Pandas already provides a built-in helper.
