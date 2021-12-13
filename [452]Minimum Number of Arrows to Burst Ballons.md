**Greedy**
---
**Basic idea**  
Find the minimum right boundary of the overlapping balloons.

**First attempt**
---
```java
class Solution {
    public int findMinArrowShots(int[][] points) {
        int count = 1;
        Arrays.sort(points, (o1, o2) -> Integer.compare(o1[0], o2[0]));

        for (int i = 1; i < points.length; i++) {
            if (points[i][0] > points[i-1][1])
                count++;
            else
                points[i][1] = Integer.min(points[i-1][1], points[i][1]);
        }
        return count;
    }
}
```
T <52.34%  
S <70.54%

**Appendix**
---
Using Lambda expression (a,b)->Integer.compare(a,b) to sort 2-dim array using Arrays.sort