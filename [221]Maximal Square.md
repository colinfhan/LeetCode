**Dynamic Programming**  
---
**Basic idea**  
Dynamic Programming Equation  
dp[i][j] = min(dp[i-1][j], dp[i][j-1], dp[i-1][j-1]) + 1  

Implementation
---
Dynamic Planning
```java
class Solution {

    public int maximalSquare(char[][] matrix) {
        int max = 0, r = matrix.length, c = matrix[0].length;
        int[][] dp = new int[r+1][c+1];
        for (int i = 0; i < r; ++i) {
            Arrays.fill(dp[i], 0);
        }
        for (int i = 1; i <= r; ++i) {
            for (int j = 1; j <= c; ++j) {
                if (matrix[i-1][j-1] == '1')
                    dp[i][j] = Math.min(Math.min(dp[i-1][j], dp[i][j-1]), dp[i-1][j-1]) + 1;
                max = Math.max(max, dp[i][j]);
            }
        }
        return max * max;
    }
}
```
**Appendix**
---
None.