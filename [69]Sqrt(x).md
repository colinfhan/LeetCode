**Binary search**  
---
**Basic idea**  
Binary search.

Implementation
---
```java
class Solution {
    public int mySqrt(int x) {
        if (x == 0) return 0;
        int l=1, r=x, mid, quotient;
        while (l<=r) {
            mid = l + (r-l)/2;
            quotient = x / mid;
            if (quotient == mid)
                return mid;
            if (quotient > mid)
                l = mid + 1;
            else
                r = mid - 1;
        }
        return r;
    }
}
```
**Appendix**
---
Focus on the value of the intermittent point of the zone.  
Avoid entering a dead loop.  
Consider special cases.  
mid=(l+r)/2 may overflow, generally use mid=lerp(l,r,1/2)=l+(r-l)/2 instead.