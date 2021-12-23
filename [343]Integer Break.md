**Dynamic Programming**  
---
**Basic idea**  
DP 1 dim  
dp[i] = max((i-j)*j, j*dp[i-j])

Implementation
---
Dynamic Planning
```java
class Solution {
    public int integerBreak(int n) {
        int[] dp = new int[n+1];
        dp[0] = dp[1] = 0;
        dp[2] = 1;
        for (int i = 3; i <= n; ++i) {
            for (int j = 2; j < i; ++j) {
                dp[i] = Math.max(Math.max((i-j)*j, dp[i]), j*dp[i-j]);
            }
        }
        return dp[n];
    }
}
```
Mathematical patterns
```java
class Solution {
    public int integerBreak(int n) {
        switch (n) {
            case 2:
                return 1;
            case 3:
                return 2;
            case 4:
                return 4;
        }
        int count = n / 3;
        int left = n % 3;
        return switch (left) {
            case 0->(int)Math.pow(3, count);
            case 1->(int)Math.pow(3, count-1)*4;
            default->(int)Math.pow(3, count)*2;
        };
    }
}
```
**Appendix**
---
None.