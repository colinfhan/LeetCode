**Dynamic Programming**  
---  
**Basic idea**  
Stock problem

Implementation
---
Dynamic Planning
```java
class Solution {
    public int maxProfit(int[] prices) {
        int min = Integer.MAX_VALUE;
        int ret = Integer.MIN_VALUE;
        for (int i = 0; i < prices.length; ++i) {
            min = Math.min(min, prices[i]);
            ret = Math.max(ret, prices[i] - min);
        }
        return ret;
    }
}
```
**Appendix**
---
None.