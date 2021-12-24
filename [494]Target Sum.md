**Dynamic Programming**  
---
**Basic idea**  
0-1

Implementation
---
```java
class Solution {
    public int findTargetSumWays(int[] nums, int target) {
        double negd = 0.5 * (Arrays.stream(nums).sum() - target);
        int neg = (int) negd;
        if (negd != neg || negd < 0)
            return 0;
        int n = nums.length;
        int[][] dp = new int[n+1][neg+1];
        dp[0][0] = 1;
        for (int i = 1; i <= n; ++i) {
            for (int j = 0; j <= neg; ++j) {
                if (j >= nums[i-1])
                    dp[i][j] = dp[i-1][j] + dp[i-1][j-nums[i-1]];
                else
                    dp[i][j] = dp[i-1][j];
            }
        }
        return dp[n][neg];
    }
}
```
**Appendix**
---
None.