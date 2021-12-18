**Searching**  
---
**Basic idea**  
DFS.

Implementation
---
```java
class Solution {
    int[][] directions = new int[][]{{1,0}, {0,-1}, {-1,0}, {0,1}};
    public void solve(char[][] board) {
        int m = board.length, n = board[0].length;
        for (int i = 0; i < n; ++i) {
            detect(board, 0, i);
            detect(board, m-1, i);
        }
        for (int i = 0; i < m; ++i) {
            detect(board, i, 0);
            detect(board, i, n-1);
        }
        for (int i = 0; i < m; ++i) {
            for (int j = 0; j < n; ++j) {
                if (board[i][j] == 'A')
                    board[i][j] = 'O';
                else if (board[i][j] == 'O')
                    board[i][j] = 'X';
            }
        }
    }

    public void detect(char[][] board, int r, int c) {
        if (board[r][c] != 'O') {
            return;
        } else {
            board[r][c] = 'A';
        }
        for (int i = 0; i < 4; ++i) {
            int x = r + directions[i][0];
            int y = c + directions[i][1];
            if ((0<=x&&x<board.length)&&(0<=y&&y<board[0].length)&&(board[x][y]=='O')) {
                detect(board, x, y);
            }
        }
    }
}
```
**Appendix**
---
None.