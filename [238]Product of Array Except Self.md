**Math**  
---
**Basic idea**  
Math

Implementation
---
```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        int[] L = new int[n], R = new int[n], ret = new int[n];
        L[0] = R[n-1] = 1;
        for (int i = 1; i < n; ++i) {
            L[i] = nums[i-1] * L[i-1];
            R[n-1-i] = nums[n-i] * R[n-i];
        }
        for (int i = 0; i < n; ++i) {
            ret[i] = L[i] * R[i];
        }
        return ret;
    }
}
```
**Appendix**
---
None.