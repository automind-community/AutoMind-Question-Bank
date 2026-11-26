# Time Series & Datetime Question Bank Compiled by AutoMind Team

## Beginner: Parsing Datetimes & Date Ranges

Use this setup for Questions 1–10:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import pandas as pd                                        %
% import numpy as np                                         %
%                                                            %
% dates_str = pd.Series([                                    %
%     '2026-01-15', '2026-02-20', '2026-03-31',              %
%     '2026-04-10', 'invalid_date'                           %
% ])                                                         %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Convert `dates_str` to `datetime64[ns]` using `pd.to_datetime(..., errors='coerce')` so `'invalid_date'` becomes `pd.NaT`.
2. Parse non-standard date strings `['15/01/2026 14:30', '20/02/2026 09:15']` using an explicit `format='%d/%m/%Y %H:%M'`.
3. Parse Unix epoch timestamps `[1767225600, 1767312000]` (in seconds) into datetimes using `pd.to_datetime(..., unit='s')`.
4. Assemble a `datetime` column from separate integer columns `'year'`, `'month'`, `'day'` using `pd.to_datetime(df[['year', 'month', 'day']])`.
5. Generate a `DatetimeIndex` of every day in January 2026 using `pd.date_range('2026-01-01', '2026-01-31', freq='D')`.
6. Generate 12 monthly month-end timestamps starting from `'2026-01-01'` using `pd.date_range(..., periods=12, freq='ME')`.
7. Generate business-day timestamps (excluding weekends) between `'2026-05-01'` and `'2026-05-15'` using `pd.bdate_range()`.
8. Generate hourly timestamps for a 24-hour day using `freq='h'` and 15-minute intervals using `freq='15min'`.
9. Create a `PeriodIndex` of quarters for 2026 (`'2026Q1'` through `'2026Q4'`) using `pd.period_range()`.
10. Create a `TimedeltaIndex` from `'0 days'` to `'5 days'` with 12-hour steps using `pd.timedelta_range()`.


## Intermediate: The .dt Accessor & Time-Based Indexing

Use:
```python
events = pd.DataFrame({
    'ts': pd.to_datetime([
        '2026-01-05 08:15:30', '2026-01-18 14:45:00',
        '2026-02-28 23:10:15', '2026-03-15 11:00:00',
        '2026-04-01 17:30:45'
    ]),
    'val': [10, 25, 18, 42, 33]
})
```

11. Extract the `year`, `month`, `day`, and `hour` from `events['ts']` using the `.dt` accessor.
12. Extract the day of the week as an integer (`0=Monday`) using `.dt.dayofweek` and as a full name using `.dt.day_name()`.
13. Extract the ISO week number using `.dt.isocalendar().week` and the calendar quarter using `.dt.quarter`.
14. Check which timestamps fall on the last day of their month using `.dt.is_month_end`.
15. Floor all timestamps to the nearest hour using `.dt.floor('h')` and round to the nearest 15 minutes using `.dt.round('15min')`.
16. Format timestamps as strings `'YYYY/MM/DD'` using `.dt.strftime('%Y/%m/%d')`.
17. Set `'ts'` as the `DataFrame` index and slice all rows in January 2026 using partial string indexing `events_idx.loc['2026-01']`.
18. Slice all rows between `'2026-01-10'` and `'2026-03-01'` using `.loc['2026-01-10':'2026-03-01']`.
19. Filter rows that occurred during business hours (9:00 AM to 5:00 PM) using `.between_time('09:00', '17:00')`.
20. Filter rows that occurred at exact time `'11:00:00'` using `.at_time('11:00')`.


## Time Zones, Timedeltas & Date Offsets

Use:
```python
idx_utc = pd.date_range('2026-06-01 12:00', periods=5, freq='6h')
s_tz = pd.Series(range(5), index=idx_utc)
```

21. Localize the naive `DatetimeIndex` of `s_tz` to `'UTC'` using `.tz_localize('UTC')`.
22. Convert the UTC-localized `Series` to `'America/New_York'` time using `.tz_convert('America/New_York')`.
23. Remove timezone awareness while keeping local wall-clock time using `.tz_localize(None)`.
24. Handle ambiguous or nonexistent timestamps during Daylight Saving Time transitions using `ambiguous='infer'` or `nonexistent='shift_forward'`.
25. Compute the time elapsed between two datetime columns `end - start` and convert the resulting `Timedelta` to total hours using `.dt.total_seconds() / 3600`.
26. Add 5 business days to a timestamp `Series` using `pd.offsets.BDay(5)`.
27. Shift timestamps to the end of the current month using `pd.offsets.MonthEnd(0)`.
28. Shift a `DatetimeIndex` forward by 2 days without moving the data values using `s.shift(2, freq='D')`.
29. Calculate the exact age in years from a `'birth_date'` column relative to `pd.Timestamp('2026-01-01')`.
30. Filter a `DataFrame` for all events that occurred in the last 7 days relative to `df['ts'].max()`.


## Resampling & Frequency Conversion

Use this hourly DataFrame for Questions 31–45:

```python
hourly = pd.DataFrame({
    'price': np.linspace(100, 120, 48) + np.sin(np.arange(48)),
    'volume': np.random.default_rng(42).integers(10, 100, size=48)
}, index=pd.date_range('2026-01-01', periods=48, freq='h'))
```

31. Downsample `hourly` to daily frequency (`'D'`) and compute the mean `'price'` and total `'volume'`.
32. Compute daily OHLC (Open, High, Low, Close) bars for `'price'` using `hourly['price'].resample('D').ohlc()`.
33. Resample to 6-hour buckets (`'6h'`) while applying different aggregations (`'price': 'mean'`, `'volume': 'sum'`).
34. Resample to weekly frequency ending on Sunday (`'W-SUN'`) vs ending on Friday (`'W-FRI'`).
35. Upsample a daily `Series` to 6-hour frequency (`'6h'`) and forward-fill missing values using `.resample('6h').ffill()`.
36. Upsample a daily `Series` to hourly frequency and linearly interpolate between days using `.resample('h').interpolate()`.
37. Fill missing timestamps in an irregular `DatetimeIndex` by reindexing to a complete `.asfreq('h')` grid.
38. Convert a `DatetimeIndex` to a monthly `PeriodIndex` using `.to_period('M')` and back to timestamps using `.to_timestamp(how='end')`.
39. Compute the daily total volume and attach it back to every hourly row using `hourly.groupby(hourly.index.date)['volume'].transform('sum')`.
40. Resample using `label='right', closed='right'` and explain how bin labeling and boundary inclusion change.


## Advanced Time Series & Calendar Logic

41. Create a custom business day offset excluding a list of holidays using `pd.offsets.CustomBusinessDay(holidays=[...])`.
42. Group a `DatetimeIndex` `DataFrame` by both `'year'` and `'month'` in one `groupby` using `df.groupby([df.index.year, df.index.month])` or `pd.Grouper(freq='ME')`.
43. Use `pd.Grouper(key='ts', freq='W')` inside `.groupby(['region', pd.Grouper(key='ts', freq='W')])` to resample within groups.
44. Compute year-over-year (YoY) percentage change on a monthly time series using `.pct_change(periods=12)`.
45. Compute month-to-date (MTD) cumulative sum within each month using `groupby(df.index.to_period('M')).cumsum()`.


## Challenge Questions: Real-World Temporal Pipelines

46. **Business-Day SLA Breach**: Given `'created_at'` and `'resolved_at'` timestamps, compute the number of business days elapsed using `np.busday_count()` and flag tickets exceeding 3 business days.
47. **Irregular Sensor Regridding**: Given irregularly spaced sensor readings, resample to an exact 5-minute grid, interpolate gaps up to 15 minutes (`limit=3`), and leave larger gaps as `NaN`.
48. **Multi-Timezone Normalization**: Given a `DataFrame` with `'local_time'` (naive) and `'timezone'` (e.g., `'US/Eastern'`, `'Europe/London'`, `'Asia/Tokyo'`), convert all timestamps into a single `'UTC'` column.
49. **Trading Session Filtering**: Filter a 1-minute stock tick `DataFrame` (in `'America/New_York'` time) to keep only regular market hours (`09:30` to `16:00`) on weekdays (`dayofweek < 5`).
50. **Active Subscriptions Per Day**: Given a table of subscriptions with `start_date` and `end_date`, compute the count of active subscriptions on every calendar day in 2026 without an explicit Python loop over days.

---

Try solving as many questions as possible using `pd.to_datetime()`, `.dt`, `.resample()`, `pd.Grouper()`, `.tz_localize()`, `.tz_convert()`, and `pd.offsets` without Python `for` loops.
