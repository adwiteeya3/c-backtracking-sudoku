# Sudoku
A Sudoku-solving algorithm using backtracking.

Sudoku is a 9x9 matrix filled with numbers 1 to 9 in such a way that every row, column and sub-matrix (3x3) has each of the digits from 1 to 9. We are provided with a partially filled 9x9 matrix and have to fill every remaining cell in it.

### Wrongly filled Sudoku
A Sudoku is considered wrongly filled if it satisfies any of these criteria:
* Any row contains the same number more than once.
* Any column contains the same number more than once.
* Any 3x3 sub-matrix has the same number more than once.

### Steps for a sudoku solver algorithm
* If there are no unallocated cells, then the Sudoku is already solved. We will just return true.
* Or else, we will fill an unallocated cell with a digit between 1 to 9 so that there are no conflicts in any of the rows, columns, or the 3x3 sub-matrices.
* Now, we will try to fill the next unallocated cell and if this happens successfully, then we will return true.
* Else, we will come back and change the digit we used to fill the cell. If there is no digit which fulfills the need, then we will just return false as there is no solution of this Sudoku.

### Code explanation
#### print_sudoku() 
> This is just a function to print the matrix

#### number_unassigned
> This function finds a vacant cell and makes the variables ‘row’ and ‘col’ equal to indices of that cell. In C, we have used pointers to change the value of the variables (row, col) passed to this function (pass by reference). In Java and Python, we are returning an array (or list, for Python) which contains these values. So, this function tells us if there is any unallocated cell or not. And if there is any unallocated cell then this function also tells us the indices of that cell

#### is_safe(int n, int r, int c)
> This function checks if we can put the value ‘n’ in the cell (r, c) or not. We are doing so by first checking if there is any cell in the row ‘r’ with the value ‘n’ or not – if(matrix[r][i] == n). Then we are checking if there is any cell with the value ‘n’ in the column ‘c’ or not – if(matrix[i][c] == n). And finally, we are checking for the sub-matrix. (r/3)*3 gives us the starting index of the row r. For example, if the value of ‘r’ is 2 then it is in the sub-matrix which starts from (0, 0). Similarly, we are getting the value of starting column by (c/3)*3. Thus, if a cell is (2,2), then this cell will be in a sub-matrix which starts from (0,0) and we are getting this value by (c/3)*3 and (r/3)*3. After getting the starting indices, we can easily iterate over the sub-matrix to check if the we can put the value ‘n’ in that sub-matrix or not.

#### solve_sudoku()
> This is the actual function which solves the Sudoku and uses backtracking. We are first checking if there is any unassigned cell or not by using the number_unassigned function and if there is no unassigned cell then the Sudoku is solved. number_unassigned function also gives us the indices of the vacant cell. Thus, if there is any vacant cell then we will try to fill this cell with a value between 1 to 9. And we will use the is_safe to check if we can fill a particular value in that cell or not. After finding a value, we will try to solve the rest of the Sudoku solve_sudoku. If this value fails to solve the rest, we will come back and try another value for this cell matrix[row][col]=0;. The loop will try other values in the cell.
