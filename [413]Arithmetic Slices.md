**Dynamic Programming**  
---
**Basic idea**  
Dynamic Programming Equation  
nums[i] - nums[i-1] == nums[i-1] - nums[i-2]
Implementation
---
Dynamic Planning
```java
class Solution {
    //Dynamic Programming Equation
    //nums[i] - nums[i-1] == nums[i-1] - nums[i-2]
    public int numberOfArithmeticSlices(int[] nums) {
        int length = nums.length;
        if (length < 3)
            return 0;
        int[] dp = new int[length];
        for (int i = 2; i < length; ++i) {
            if (nums[i] - nums[i-1] == nums[i-1] - nums[i-2])
                dp[i] = dp[i-1] + 1;
        }
        return Arrays.stream(dp).sum();
    }
}
```
**Appendix**
---
None.