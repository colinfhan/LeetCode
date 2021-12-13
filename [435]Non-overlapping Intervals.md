**Greedy**  
---
**Basic idea**  
Sorting by interval ending size in ascending order, using a greedy strategy.  

**First attempt**
---
```java
class Solution {
    public int eraseOverlapIntervals(int[][] intervals) {
        Arrays.sort(intervals, (o1, o2) -> o1[1] - o2[1]);
        int end = intervals[0][1];
        int result = 0;
        for (int i = 1; i < intervals.length; i++) {
            if (intervals[i][0]>=end)
                end = intervals[i][1];
            else
                result++;
        }
        return result;
    }
}
```
T <94.61%  
S <90.12%

**Appendix**
---
Using Lambda expression to sort 2-dim array using Arrays.sort