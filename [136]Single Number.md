**Bit Manipulation**  
---
**Basic idea**  
XOR

Implementation
---
```java
class Solution {
    public int singleNumber(int[] nums) {
        int ret = 0;
        for(int i:nums) {
            ret ^= i;
        }
        return ret;
    }
}
```
**Appendix**
---
x ^ 0 = x, x ^ x = 0, x ^ y ^ x ^ 0 = y.