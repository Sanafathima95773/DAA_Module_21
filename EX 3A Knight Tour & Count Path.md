# EX 3A Knight Tour & Count Path
## DATE:
## AIM:
To write a python program to find minimum steps to reach to specific cell in minimum moves by knight


## Algorithm
1. Define the dimensions of the matrix R and C (rows and columns), and set MAX_K as the maximum value for k.
2. Define a recursive function pathCountDPRecDP that computes the number of paths to reach the bottom-right corner from the top-left corner, with the exact sum k.
3. If m < 0, n < 0, or k < 0, return 0 as these are invalid paths.
4. If the current cell (m, n) is the top-left corner (0, 0) and the sum k equals mat[m][n], return 1 (a valid path).
5. If the result for the current state (m, n, k) is already computed (i.e., dp[m][n][k] != -1), return the cached result.
6. Otherwise, recursively compute the number of paths by considering two possible moves:
(I)Move up by decreasing m by 1, with the new sum being k - mat[m][n].
(II)Move left by decreasing n by 1, with the new sum being k - mat[m][n].
7. Store the result of the recursive calls in dp[m][n][k].
8. Define the function pathCountDP that calls pathCountDPRecDP starting from the bottom-right corner (R - 1, C - 1) with the target sum k.
9. Initialize the dp table with all values set to -1 to indicate that no values have been computed.
10.Call the pathCountDP function with the matrix and the target sum k, and print the result.  

## Program:
```
Program to implement to find minimum steps to reach to specific cell in minimum moves by knight.
Developed by: Sana Fathima H
Register Number: 212223240145
R = 3
C = 3
MAX_K = 1000
def pathCountDPRecDP(mat, m, n, k):
    if m < 0 or n < 0 or k < 0:
        return 0
    elif m == 0 and n == 0:
        return k == mat[m][n]
    if (dp[m][n][k] != -1):
        return dp[m][n][k]
    dp[m][n][k] = (pathCountDPRecDP(mat, m - 1, n, k - mat[m][n]) +
                   pathCountDPRecDP(mat, m, n - 1, k - mat[m][n]))
     
    return dp[m][n][k]
def pathCountDP(mat, k):
    return pathCountDPRecDP(mat, R - 1, C - 1, k)
k = 12
dp = [[ [-1 for col in range(MAX_K)]
            for col in range(C)]
            for row in range(R)]
mat = [[1, 2, 3],
       [4, 6, 5],
       [3, 2, 1]]
print(pathCountDP(mat, k))  


```

## Output:
![image](https://github.com/user-attachments/assets/dcf26213-71e6-42d5-b4b0-249917a133d4)


## Result:
The program executed successfully, and the minimum number of steps for the knight to reach the target was calculated.
