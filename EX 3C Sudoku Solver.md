# EX 3C Sudoku Solver
## DATE:
## AIM:
To write a python program to find the solution of sudoku puzzle using Backtracking.


## Algorithm
1. Start from the first empty cell on the board.
2. Try placing values from 1 to 9 in the cell, one by one.
3. For each value, check if placing it violates Sudoku rules (row, column, and subgrid uniqueness).
4. If a valid value is found, place it and recursively try to solve the next empty cell.
5. If no value is valid, backtrack by resetting the cell and trying the next possible value.
6. Continue until the board is completely filled or no solution exists.  

## Program:
```
Program to implement to to find the solution of sudoku puzzle using Backtracking.
Developed by: Sana Fathima H
Register Number:  212223240145
board = [
    [0, 0, 0, 8, 0, 0, 4, 0, 3],
    [2, 0, 0, 0, 0, 4, 8, 9, 0],
    [0, 9, 0, 0, 0, 0, 0, 0, 2],
    [0, 0, 0, 0, 2, 9, 0, 1, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 7, 0, 6, 5, 0, 0, 0, 0],
    [9, 0, 0, 0, 0, 0, 0, 8, 0],
    [0, 6, 2, 7, 0, 0, 0, 0, 1],
    [4, 0, 3, 0, 0, 6, 0, 0, 0]
]

def printBoard(board):
    for i in range(0, 9):
        for j in range(0, 9):
            print(board[i][j], end=" ")
        print()

def isPossible(board, row, col, val):
    for j in range(0, 9):
        if board[row][j] == val:
            return False

    for i in range(0, 9):
        if board[i][col] == val:
            return False

    startRow = (row // 3) * 3
    startCol = (col // 3) * 3
    for i in range(0, 3):
        for j in range(0, 3):
            if board[startRow+i][startCol+j] == val:
                return False
    return True

def solve():
    for i in range(0, 9):
        for j in range(0, 9):
            if board[i][j] == 0:
                for val in range(1, 10):
                    if isPossible(board, i, j, val):
                        board[i][j] = val
                        solve()
                        board[i][j] = 0
                return
    printBoard(board)

solve()
```

## Output:
![image](https://github.com/user-attachments/assets/2752701c-7ed1-4b9e-ab93-3d06043312f0)



## Result:
The Sudoku solver program executed successfully and found the solution for the given puzzle.
