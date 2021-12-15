**Binary search**  
---
**Basic idea**  
Binary search - Rotating arrays.

Implementation
---
```java
class Solution {
    public int findMin(int[] nums) {
        int l = 0, r = nums.length-1, mid, ret = nums[0];
        while (l <= r) {
            mid = l + (r - l) / 2;
            if (nums[l] == nums[mid]) {
                ret = Integer.min(ret, nums[l]);
                ++l;
            }
            else {
                if (nums[mid] > nums[l]) {
                    ret = Integer.min(ret, nums[l]);
                    l = mid + 1;
                } else {
                    ret = Integer.min(ret, nums[mid]);
                    r = mid - 1;
                }
            }
        }
        return ret;
    }
}
```
**Appendix**
---
Focus on whether there is an equal sign in the loop end condition.