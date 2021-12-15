**Binary search**  
---
**Basic idea**  
Binary search - Rotating arrays.

Implementation
---
```java
class Solution {
    public boolean search(int[] nums, int target) {
        int l = 0, r = nums.length - 1, mid = -1;
        while (l <= r) {
            mid = l + (r - l) / 2;
            if (nums[mid] == target)
                return true;
            if (nums[mid] == nums[l])
                ++l;
            else if (nums[mid] > nums[l]) {
                if (nums[l] <= target && target < nums[mid])
                    r = mid - 1;
                else
                    l = mid + 1;
            }
            else {
                if (nums[mid] < target && target <= nums[r])
                    l = mid + 1;
                else
                    r = mid - 1;
            }
        }
        return false;
    }
}
```
**Appendix**
---
Discussion by situation.