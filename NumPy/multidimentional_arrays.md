## NumPy Multidimentional Array Question Bank Compiled By AutoMind Team 

## Beginner  Creating & Inspecting Arrays

1. Create a 2D NumPy array with 3 rows and 4 columns containing the numbers 1–12.
2. Create a 3D NumPy array with shape (2, 3, 4) containing numbers from 1 to 24.
3. Create a 4×5 array filled entirely with zeros.
4. Create a 3×3 array filled entirely with ones.
5. Create a 5×5 identity matrix using NumPy.
6. Create a 3D array of shape (2, 4, 3) filled with random integers between 1 and 50.
7. Given a NumPy array, write code to print its number of dimensions using .ndim.
8. Given a multidimensional array, write code to print its shape, size, and data type.
9. Create an array with shape (2, 3, 4) and reshape it into (4, 6).
10. Create a 2D array containing numbers 1–20 and reshape it into 4 rows and 5 columns.

## Indexing & Slicing

11. Given 
arr = np.array([
    [10, 20, 30, 40],
    [50, 60, 70, 80],
    [90, 100, 110, 120]
])
Extract the element 70.
12. Extract the entire second row from the array above.
13. Extract the entire third column.

14. Extract the Subarray
20 30
60 70
100 110

15. Extract the last two rows and last two columns of a 2D array.
16. Given a 3D array with shape (2, 3, 4), extract the first 2D matrix.
17. From a 3D array, extract the second row of the first matrix.
18. From a 3D array with shape (2, 3, 4), extract all elements from the third column of every row in every matrix.
19. Reverse all rows of a 2D NumPy array.
20. Reverse both the rows and columns of a 2D array.

## Array Operations

21. Create two 3×3 arrays and calculate their element-wise sum.
22. Create two 3×3 arrays and calculate their element-wise difference.
23. Multiply two 3×3 arrays element by element.
24. Divide every element of a 2D array by 5.
25. Square every element of a multidimensional array.
26. Find the maximum value in a 3D array.
27. Find the minimum value in a 3D array.
28. Calculate the sum of all elements in a 3D array.
29. Calculate the mean of all elements in a 2D array.
30. Find the maximum value of each row in a 2D array.


## Axis-Based Operations
31. Given a 4×5 array, calculate the sum of each row using the appropriate axis.
32. Calculate the sum of each column of a 4×5 array.
33. Find the mean of each row.
34. Find the mean of each column.
35. Given a 3D array, calculate the sum along axis=0.
36. Given a 3D array, calculate the sum along axis=1.
37. Given a 3D array, calculate the sum along axis=2.
38. Find the maximum value along each row of a 2D array and return the resulting 1D array.
39. Find the index of the maximum value in each row using np.argmax().
40. Find the index of the minimum value in each column using np.argmin().

## Intermediate / Advanced Challenges
41. Given a 5×5 array, replace every value greater than 20 with 0 using Boolean indexing.
42. Given a 4×4 array, replace all even numbers with -1.
43. Given a multidimensional array, count how many elements are greater than 50.
44. Given a 3D array, find all elements that are divisible by 3.
45. Given two 2D arrays, vertically stack them using NumPy.
46. Given two 2D arrays with compatible dimensions, horizontally stack them.
47. Transpose a 2D array without using a Python for loop.
48. Perform matrix multiplication between two compatible 2D NumPy arrays using np.matmul() or @.
49. Given a 3D array representing:
2 students × 3 subjects × 4 test scores
50. Challenge: Given a 3D array representing:
5 students × 4 subjects × 3 exams
write NumPy code to:

- calculate each student's average score,
- calculate each subject's average score,
- find the highest individual score,
- find the student with the highest overall average,
- find the subject with the lowest average,
- and replace every score below 40 with 0.
