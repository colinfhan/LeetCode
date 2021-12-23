**Dynamic Programming**  
---
**Basic idea**  
DP 1 dim  
dp[i]=max(dp[i-1], dp[i-2]+nums[i])
0->n-2, 1->n-1
Implementation
---
Dynamic Planning
```java
class Solution {
    public int rob(int[] nums) {
        int n = nums.length;
        if (n==1)
            return nums[0];
        int[] dp = new int[n];
        dp[1] = nums[0];
        for (int i = 2; i <= n-1; ++i) {
            dp[i] = Math.max(dp[i-1], dp[i-2]+nums[i-1]);
        }
        int ret = dp[n-1];
        dp = new int[n];
        dp[1] = nums[1];
        for (int i = 2; i <= n-1; ++i) {
            dp[i] = Math.max(dp[i-1], dp[i-2]+nums[i]);
        }
        ret = Math.max(ret, dp[n-1]);
        return ret;
    }
}
```
**Appendix**
---
None.