**Searching**  
---
**Basic idea**  
Backtracing.

Implementation
---
```java
class Solution {
    public List<List<String>> solveNQueens(int n) {
        List<List<String>> ret = new ArrayList<>();
        boolean[] col = new boolean[n], ldiag = new boolean[2*n-1], rdiag = new boolean[2*n-1];
        Arrays.fill(col, false);
        Arrays.fill(ldiag, false);
        Arrays.fill(rdiag, false);
        char[][] board = new char[n][n];
        for (int i = 0; i < n; ++i) {
            Arrays.fill(board[i], '.');
        }
        backtracking(n, col, ldiag, rdiag, ret, 0, board);
        return ret;
    }
    public void backtracking(int n, boolean[] col, boolean[] ldiag, boolean[] rdiag, List<List<String>> ret, int row, char[][] board) {
        if (row == n) {
            List<String> bingo = new ArrayList<>();
            for (int i = 0; i < n; ++i)
                bingo.add(String.valueOf(board[i]));
            ret.add(bingo);
            return;
        }
        for (int i = 0; i < n; ++i) {
            int pl = row + i, pr = row + n - i - 1;
            if (col[i] || ldiag[pl] || rdiag[pr])
                continue;
            col[i] = ldiag[pl] = rdiag[pr] = true;
            board[row][i] = 'Q';
            backtracking(n, col, ldiag, rdiag, ret, row + 1, board);
            col[i] = ldiag[pl] = rdiag[pr] = false;
            board[row][i] = '.';
        }
    }
}
```
**Appendix**
---
In backtracking algorithms, permutation problems are generally solved by swapping positions, and combination problems are generally solved by moving numbers into/out of sets.