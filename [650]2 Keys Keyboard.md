**Dynamic Programming**  
---
**Basic idea**
Dynamic Programming Equation  
dp[i] = min(dp[i], dp[j]+i/j)  

Implementation
---
Dynamic Planning
```java
class Solution {
    public int minSteps(int n) {
        int[] dp = new int[n+1];
        for (int i = 2; i <= n; ++i) {
            dp[i] = i;
            for (int j = 2; j < i; ++j) {
                if (i%j==0)
                    dp[i] = Math.min(dp[i], dp[j]+i/j);
            }
        }
        return dp[n];
    }
}
```
**Appendix**
---
None.