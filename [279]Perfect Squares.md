**Dynamic Programming**  
---
**Basic idea**  
Dynamic Programming Equation  
dp[i] = min(dp[i-1], dp[i-4], dp[i-9]....) + 1  


Implementation
---
Dynamic Planning
```java
class Solution {
    public int numSquares(int n) {
        int[] dp = new int[n+1];
        Arrays.fill(dp, 0);
        for (int i = 1; i <= n; ++i) {
            int min = Integer.MAX_VALUE - 1;
            for (int j = 1; j <= Math.sqrt(i); ++j) {
                min = Math.min(dp[i-j*j], min);
            }
            dp[i] = min + 1;
        }
        return dp[n];
    }
}
```
**Appendix**
---
None.