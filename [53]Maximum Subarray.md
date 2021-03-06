**Dynamic Programming**  
---
**Basic idea**  
DP 1 dim  
dp[i] = max(dp[i-1]+nums[i], nums[i])  

Implementation
---
Dynamic Planning
```java
class Solution {
    public int maxSubArray(int[] nums) {
        int n = nums.length;
        if (n==1)
            return nums[0];
        int[] dp = new int[n];
        dp[0] = nums[0];
        for (int i = 1; i < n; ++i) {
            dp[i] = Math.max(dp[i-1]+nums[i], nums[i]);
        }
        return Arrays.stream(dp).max().getAsInt();
    }
}
```
**Appendix**
---
None.