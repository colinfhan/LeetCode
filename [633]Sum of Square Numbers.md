**Two pointer**  
---
**Basic idea**  
Discover mathematical patterns.

Implementation
---
```java
class Solution {
    public boolean judgeSquareSum(int c) {
        for (long i = 0; i*i <= c; i++) {
            double j = Math.sqrt(c - i*i);
            if ((int)j == j)
                return true;
        }
        return false;
    }
}
```
**Appendix**
---
Make good use of forward and backward extrapolation.  
Keep an eye on the data range at all times.