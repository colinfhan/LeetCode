**Greedy**  
---
**Basic idea**  
Look for greedy strategies and try them later

**Implementation **
---
```java
class Solution {
    public int maxProfit(int[] prices) {
        int curret = prices[0];
        int total = 0;
        for (int i = 1; i < prices.length; i++) {
            if (prices[i]<prices[i-1]) {
                total += prices[i - 1] - curret;
                curret = prices[i];
            }
        }
        if (prices[prices.length-1]>curret)
            total += prices[prices.length-1] - curret;
        return total;
    }
}
```
**Appendix**
---
Note the boundary condition control