**Dynamic Programming**  
---
**Basic idea**  
Dynamic Programming Equation  
dp[i] = dp[i-1] + dp[i-2] or dp[i-2] or dp[i-1]  

Implementation
---
Dynamic Planning
```java
class Solution {
    public int numDecodings(String s) {
        int length = s.length();
        int[] dp = new int[length + 1];
        Arrays.fill(dp, 1);
        int pre = s.charAt(0) - '0';
        if (pre==0)
            return 0;
        for (int i = 2; i <= length; ++i) {
            int cur = s.charAt(i-1) - '0';
            if ((pre!=1 && pre!=2) && cur==0)
                return 0;
            if (10<=(pre*10+cur) && (pre*10+cur)<=26) {
                if (cur!=0)
                    dp[i] = dp[i-1] + dp[i-2];
                else
                    dp[i] = dp[i-2];
            } else
                dp[i] = dp[i-1];
            pre = cur;
        }
        return dp[length];
    }
}
```
**Appendix**
---
None.