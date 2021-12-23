**Dynamic Programming**  
---
**Basic idea**  
0-1 knapsack  
Dynamic Programming Equation  
dp[i][j][k] = max(dp[i-1][j][k], dp[i-1][j-counts[0]][k-counts[1]]+1)  

Implementation
---
Dynamic Planning
```java
class Solution {
    public int findMaxForm(String[] strs, int m, int n) {
        int length = strs.length;
        int[][][] dp = new int[length+1][m+1][n+1];
        for (int i = 0; i < m+1; ++i) {
            Arrays.fill(dp[0][i], 0);
        }
        for (int i = 1; i < length+1; ++i) {
            int[] counts = count(strs[i-1]);
            for (int j = 0; j < m+1; ++j) {
                for (int k = 0; k < n+1; ++k) {
                    if (j>=counts[0]&&k>=counts[1])
                        dp[i][j][k] = Math.max(dp[i-1][j][k], dp[i-1][j-counts[0]][k-counts[1]]+1);
                    else
                        dp[i][j][k] = dp[i-1][j][k];
                }
            }
        }
        return dp[length][m][n];
    }

    public int[] count(String str) {
        int[] ret = new int[2];
        int ones = 0, zeros = 0;
        for(char i:str.toCharArray())
            if (i=='0')
                ++zeros;
            else
                ++ones;
        ret[0] = zeros;
        ret[1] = ones;
        return ret;
    }
}
```
**Appendix**
---
None.