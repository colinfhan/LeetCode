**Data Structure**  
---
**Basic idea**  
Array

Implementation
---
```java
class Solution {
    public int maxChunksToSorted(int[] arr) {
        int max = -1, count = 0;
        for (int i=0; i<arr.length; ++i) {
            max = Math.max(max, arr[i]);
            if (max == i)
                ++count;
        }
        return count;
    }
}
```
**Appendix**
---
None.