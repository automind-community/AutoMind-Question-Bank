## Slicing Question Bank Compiled by AutoMind Team

## Beginner: 1D Array Slicing

Use this array for Questions 1–10:
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% import numpy as np                                         %
%                                                            %
% arr = np.array([10, 20, 30, 40, 50, 60, 70, 80, 90, 100])  %
%                                                            %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

1. Extract the first 5 elements from arr.
2. Extract the last 5 elements from arr.
3. Extract elements from index 2 to index 6.
4. Extract elements from index 3 to the end.
5. Extract elements from the beginning up to index 5.
6. Extract every second element from arr.
7. Extract every third element from arr.
8. Reverse the entire array using slicing.
9. Extract the last 4 elements in reverse order.
10. Extract elements from index 1 through index 8 with a step of 2.


## Intermediate: 1D Slicing

Use:
arr = np.arange(1, 21)

11. Extract the first 10 elements.
12. Extract the numbers from 5 through 15.
13. Extract all even-positioned elements using slicing.
14. Extract all odd-positioned elements using slicing.
15. Reverse the array.
16. Extract the last 10 elements in reverse order.
17. Extract every third element starting from index 1.
18. Extract elements at indices 2, 5, 8, 11, 14, and so on using slicing.
19. Extract the first half of the array.
20. Extract the second half of the array.

## 2D Array Slicing

Use this array for Questions 21–35:

arr = np.array([
    [ 1,  2,  3,  4,  5],
    [ 6,  7,  8,  9, 10],
    [11, 12, 13, 14, 15],
    [16, 17, 18, 19, 20],
    [21, 22, 23, 24, 25]
])

21. Extract the first row.
22. Extract the last row.
23. Extract the first column.
24. Extract the last column.
25. Extract the first 3 rows.
26. Extract the last 2 rows.
27. Extract the first 3 columns.
28. Extract the last 2 columns
29. Extract the subarray containing:
7   8   9
12  13  14
17  18  19
30. Extract the center 3×3 portion of the array.
31. Extract the top-left 2×2 portion.
32. Extract the bottom-right 2×2 portion.
33. Extract every second row.
34. Extract every second column.
35. Extract every second row and every second column simultaneously.

## Advanced 2D Slicing

36. Reverse the order of all rows.
37. Reverse the order of all columns.
38. Reverse both rows and columns.
39. Extract the first 3 rows while taking every second column.
40. Extract the last 3 rows while taking every second column in reverse order.
41. Extract the first 4 rows and reverse the columns.
42. Extract the last 4 columns and reverse the rows.
43. Extract the pattern using slicing 
 1   3   5
11  13  15
21  23  25
44. Extract this pattern
25 23 21
15 13 11
 5  3  1
45. Using only slicing, exchange the order of the rows so that the last row appears first and the first row appears last.

## 3D Array Slicing
Use:
arr = np.arange(1, 25).reshape(2, 3, 4)

array has shape (2,3,4)

46. Extract the first 2D array from the 3D array.
47. Extract the second 2D array.
48. Extract the first row from both 2D arrays.
49. Extract the last two columns from every row of every 2D array.
50. Extract every second element along the last dimension of the 3D array.

## Challenge Questions


51. Extract the four corners of a 2D array.
52. Extract the border of a 2D array using slicing.
53. Extract every other row in reverse order.
54. Extract every other column in reverse order.
55. From a 3D array, extract the last matrix, last two rows, and first two columns in one slicing expression.

Try solving as many questions as possible using only : and integer slice notation, without np.delete(), np.take(), or loops.