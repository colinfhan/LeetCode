**Greedy**  
---
**Basic idea**  
Sort first, then find mathematical relationships

**Implementation **
---
```java
class Solution {
    public int[][] reconstructQueue(int[][] people) {
        Arrays.sort(people, (x,y)-> x[0] != y[0] ? Integer.compare(x[0], y[0]) : Integer.compare(y[1], x[1]));
        int[][] ans = new int[people.length][];
        for (int[] person : people) {
            int spaces = person[1] + 1;
            for (int i = 0; i < people.length; ++i) {
                if (ans[i] == null) {
                    --spaces;
                    if (spaces == 0) {
                        ans[i] = person;
                        break;
                    }
                }
            }
        }
        return ans;
    }
}
```
**Appendix**
---
Greedy algorithms many times have to process the input data first.