**Bit Manipulation**  
---
**Basic idea**  
xor

Implementation
---
```java
class Solution {
    public int missingNumber(int[] nums) {
        int ret = 0;
        for(int i:nums) {
            ret ^= i;
        }
        for(int i=0; i<=nums.length; ++i) {
            ret ^= i;
        }
        return ret;
    }
}
```
**Appendix**
---
None.