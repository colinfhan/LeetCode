**Dynamic Programming**  
---
**Basic idea**  
DP 1 dim  
dp[i]=max(dp[i-1], dp[i-2]+nums[i])
Implementation
---
Dynamic Planning
```java
class Solution {
    //dp[i]=max(dp[i-1], dp[i-2]+nums[i])
    public int rob(int[] nums) {
        int n = nums.length;
        if (n==1)
            return nums[0];
        if (n==2)
            return Math.max(nums[0], nums[1]);
        int[] dp = new int[n];
        dp[0]=nums[0];
        dp[1]=Math.max(nums[0], nums[1]);
        for (int i = 2; i < n; ++i) {
            dp[i] = Math.max(dp[i-1], dp[i-2]+nums[i]);
        }
        return dp[n-1];
    }
}
```
Optimizing space complexity
```java
class Solution {
    //dp[i]=max(dp[i-1], dp[i-2]+nums[i])
    public int rob(int[] nums) {
        int n = nums.length;
        if (n==1)
            return nums[0];
        int pre1=0, pre2=0, current = 0;
        for (int i = 0; i < n; ++i) {
            current = Math.max(pre2, pre1+nums[i]);
            pre1 = pre2;
            pre2 = current;
        }
        return current;
    }
}
```
**Appendix**
---
None.