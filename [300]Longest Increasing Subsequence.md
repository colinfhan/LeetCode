**Dynamic Programming**  
---
**Basic idea**  
Dynamic Programming Equation  
dp[i] = Math.max(dp[i], dp[j]+1)  

Implementation
---
Dynamic Planning
```java
class Solution {
    public int lengthOfLIS(int[] nums) {
        int n = nums.length;
        int[] dp = new int[n];
        Arrays.fill(dp, 1);
        int max = Integer.MIN_VALUE;
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < i; ++j) {
                if (nums[i] > nums[j])
                    dp[i] = Math.max(dp[i], dp[j]+1);
            }
            max = Math.max(max, dp[i]);
        }
        return max;
    }
}
```
**Appendix**
---
None.