**Math**  
---
**Basic idea**  
Math - Boyer-Moore Majority Vote

Implementation
---
```java
class Solution {
    public int majorityElement(int[] nums) {
        int candidate = 0, count = 0;
        for (int i:nums) {
            if (count == 0)
                candidate = i;
            count += i == candidate ? 1 : -1;
        }
        return candidate;
    }
}
```
**Appendix**
---
None.