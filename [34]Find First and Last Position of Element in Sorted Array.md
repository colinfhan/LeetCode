**Binary search**  
---
**Basic idea**  
Binary search - Interval search.

Implementation
---
```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int l=0, r=nums.length-1, mid=-1, pos=-1;
        while (l<=r) {
            mid = l + (r-l) / 2;
            if (nums[mid] == target) {
                pos = mid;
                break;
            }
            if (nums[mid] > target)
                r = mid - 1;
            else
                l = mid + 1;
        }
        if (pos == -1)
            return new int[]{-1, -1};
        else {
            int low = pos, high = pos;
            while (low >= 0 && nums[low] == target)
                --low;
            while (high < nums.length && nums[high] == target)
                ++high;
            return new int[] {low+1, high-1};
        }
    }
}
```
**Appendix**
---
None.