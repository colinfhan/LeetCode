**Dynamic Programming**  
---  
**Basic idea**  
Stock problem with State Machine

Implementation
---
Dynamic Planning
```java
class Solution {
    public int maxProfit(int[] prices) {
        int n = prices.length;
        int[] buy = new int[n], s1 = new int[n], sell = new int[n], s2 = new int[n];
        buy[0] = s1[0] = -prices[0];
        for (int i = 1; i < n; ++i) {
            buy[i] = s2[i-1] - prices[i];
            s1[i] = Math.max(s1[i-1], buy[i-1]);
            sell[i] = Math.max(buy[i-1] + prices[i], s1[i-1] + prices[i]);
            s2[i] = Math.max(sell[i-1], s2[i-1]);
        }
        return Math.max(s2[n-1], sell[n-1]);
    }
}
```
**Appendix**
---
None.