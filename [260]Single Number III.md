**Bit Manipulation**  
---
**Basic idea**  
xor

Implementation
---
```java
class Solution {
    public int[] singleNumber(int[] nums) {
        int all = 0;
        for(int i:nums)
            all ^= i;
        int test = 1;
        while ((all & test) == 0)
            test <<= 1;
        int x = 0, y = 0;
        for(int i:nums) {
            if ((i & test) == 0)
                x ^= i;
            else
                y ^= i;
        }
        return new int[]{x, y};
    }
}
```
**Appendix**
---
None.