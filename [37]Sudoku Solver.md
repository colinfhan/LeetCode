**Searching**  
---
**Basic idea**  
Backtracing.

Implementation
---
```java
class Solution {
    boolean found = false;
    public void solveSudoku(char[][] board) {
        int[][] row = new int[9][9], col = new int[9][9], sub = new int[9][9];
        for (int i = 0; i < 9; ++i) {
            Arrays.fill(row[i], 0);
            Arrays.fill(col[i], 0);
            Arrays.fill(sub[i], 0);
        }
        for (int i = 0; i < 9; ++i) {
            for (int j = 0; j < 9; ++j) {
                char c = board[i][j];
                int I = i/3;
                int J = j/3;
                int C = (int) c - '1';
                if ('1'<= c && c <= '9') {
                    row[i][C] = -1;
                    col[j][C] = -1;
                    sub[J*3+I][C] = -1;
                }
            }
        }
        backtracking(board, row, col, sub, 0, 0);
    }

    public void backtracking(char[][] board, int[][] row, int[][] col, int[][] sub, int r, int c) {
        if (found)
            return;
        if (r==9) {
            found = true;
            return;
        }
        int y = c + 1;
        int x = r;
        if (y > 8) {
            y -= 9;
            ++x;
        }
        if (board[r][c] == '.') {
            int R = r/3;
            int C = c/3;
            for (int i = 0; i < 9; ++i) {
                if (row[r][i] == 0 && col[c][i] == 0 && sub[R+3*C][i]==0) {
                    row[r][i] = 1; col[c][i] = 1; sub[R+3*C][i]= 1; board[r][c] = (char) (i+'1');
                    backtracking(board, row, col, sub, x, y);
                    if (found)
                        break;
                    row[r][i] = 0; col[c][i] = 0; sub[R+3*C][i]= 0; board[r][c] = '.';
                }
            }
        } else {
            backtracking(board, row, col, sub, x, y);
        }
    }
}
```
**Appendix**
---
None.