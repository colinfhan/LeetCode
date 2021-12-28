**Partitioning Algorithm**  
---
**Basic idea**  
Partitioning algorithm + dp  

Implementation
---
```java
class Solution {
    public int maxCoins(int[] nums) {
        int n = nums.length;
        int[][] dp = new int[n+2][n+2];
        int[] val = new int[n+2];
        val[0] = val[n+1] = 1;
        for (int i = 1; i < n+1; ++i) {
            val[i] = nums[i-1];
        }
        for (int i = n-1; i >= 0; --i)
            for (int j = i+2; j <= n+1; ++j)
                for (int k = i+1; k < j; ++k)
                    dp[i][j] = Math.max(dp[i][j], val[i] * val[j] * val[k] + dp[i][k] + dp[k][j]);
        return dp[0][n+1];
    }
}
```
**Appendix**
---
None.