**Dynamic Programming**  
---
**Basic idea**  
Dynamic Programming Equation  
dp[i] = dp[i] || dp[i-len]  
Implementation
---
Dynamic Planning
```java
class Solution {
    public boolean wordBreak(String s, List<String> wordDict) {
        int n = s.length();
        boolean[] dp = new boolean[n+1];
        Arrays.fill(dp, false);
        dp[0] = true;
        for (int i = 1; i <= n; ++i) {
            for (String word:wordDict) {
                int len = word.length();
                if (i>=len && s.substring(i-len, i).compareTo(word)==0)
                    dp[i] = dp[i] || dp[i-len];
            }
        }
        return dp[n];
    }
}
```
**Appendix**
---
None.