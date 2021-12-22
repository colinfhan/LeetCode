**Dynamic Programming**  
---
**Basic idea**  
0-1 knapsack  
Dynamic Programming Equation  
dp[i][j] = dp[i-1][j]||dp[i-1][j-nums[i-1]]  

Implementation
---
Dynamic Planning
```java
class Solution {
    public boolean canPartition(int[] nums) {
        int n = nums.length, sum = IntStream.of(nums).sum();
        if (sum % 2 == 1)
            return false;
        int target = sum/2;
        boolean[][] dp = new boolean[n+1][target+1];
        for (int i = 0; i < n + 1; ++i) {
            Arrays.fill(dp[i], false);
        }
        dp[0][0] = true;
        for (int i = 1; i < n+1; ++i) {
            for (int j = 1; j < target+1; ++j) {
                if (j>=nums[i-1])
                    dp[i][j] = dp[i-1][j]||dp[i-1][j-nums[i-1]];
                else
                    dp[i][j] = dp[i-1][j];
            }
        }
        return dp[n][target];
    }
}
```
**Appendix**
---
None.