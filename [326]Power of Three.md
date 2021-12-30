**Math**  
---
**Basic idea**  
Math

Implementation
---
```java
class Solution {
    public boolean isPowerOfThree(int n) {
        double ret = Math.log10(n) / Math.log10(3);
        return (int)ret == ret;
    }
}
```
**Appendix**
---
None.