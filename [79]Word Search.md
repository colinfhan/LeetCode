**Searching**  
---
**Basic idea**  
Backtracing.

Implementation
---
```java
class Solution {
    boolean flag;
    int[][] directions = new int[][]{{-1, 0}, {0, 1}, {1, 0}, {0, -1}};
    public boolean exist(char[][] board, String word) {
        int m = board.length, n = board[0].length;
        boolean[][] mark = new boolean[m][n];
        for (int i = 0; i < m; ++i) {
            Arrays.fill(mark[i], false);
        }
        flag = false;
        for (int i = 0; i < m; ++i) {
            for (int j = 0; j < n; ++j) {
                if (board[i][j] == word.charAt(0))
                    backtracking(board, word, i, j, 1, mark);
                if (flag)
                    return flag;
            }
        }
        return flag;
    }

    public void backtracking(char[][] board, String word, int r, int c, int pos, boolean[][] mark) {
        if (pos == word.length() || flag) {
            flag = true;
            return;
        }
        mark[r][c] = true;
        for (int i = 0; i < 4; ++i) {
            int x = r + directions[i][0];
            int y = c + directions[i][1];
            if ((0<=x&&x<board.length) && (0<=y&&y<board[0].length) &&
                    (!mark[x][y]) && (board[x][y] == word.charAt(pos)))
                backtracking(board, word, x, y, pos + 1, mark);
        }
        mark[r][c] = false;
    }
}
```
**Appendix**
---
In backtracking algorithms, permutation problems are generally solved by swapping positions, and combination problems are generally solved by moving numbers into/out of sets.