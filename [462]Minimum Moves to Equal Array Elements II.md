**Math**  
---
**Basic idea**  
Math - Properties of the median

Implementation
---
```java
class Solution {
    public int minMoves2(int[] nums) {
        int ret = 0, n = nums.length;
        Arrays.sort(nums);
        for (int i:nums)
            ret += Math.abs(i-nums[n/2]);
        return ret;
    }
}
```
**Appendix**
---
None.