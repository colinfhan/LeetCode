**Dynamic Programming**  
---  
**Basic idea**  
Stock problem

Implementation
---
Dynamic Planning
```java
class Solution {
    public int maxProfit(int k, int[] prices) {
        int n = prices.length;
        if (n==0)
            return 0;
        k = Math.min(k, n/2);
        int[][] buy = new int[n][k+1], sell = new int[n][k+1];
        buy[0][0] = -prices[0];
        sell[0][0] = 0;
        for (int i = 1; i <= k; ++i) {
            buy[0][i] = sell[0][i] = Integer.MIN_VALUE / 2;
        }
        for (int i = 1; i < n; ++i) {
            for (int j = 0; j <= k; ++j) {
                buy[i][j] = Math.max(buy[i-1][j], sell[i-1][j]-prices[i]);
                if (j!=0)
                    sell[i][j] = Math.max(sell[i-1][j], buy[i-1][j-1]+prices[i]);
            }
        }
        return Arrays.stream(sell[n-1]).max().getAsInt();
    }
}
```
**Appendix**
---
None.