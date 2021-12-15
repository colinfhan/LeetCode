**Binary search**  
---
**Basic idea**  
Binary search.

Implementation
---
```java
class Solution {
    public int singleNonDuplicate(int[] nums) {
        if (nums.length == 1)
            return nums[0];
        int l = 0, r = nums.length - 1, mid;
        while (l <= r) {
            mid = l + (r - l) / 2;
            if ((mid==0 && nums[mid] != nums[mid+1]) ||
                    (mid == nums.length-1 && nums[mid] != nums[mid-1]) ||
                    (nums[mid] != nums[mid-1] && nums[mid] != nums[mid+1]))
                return nums[mid];
            if ((mid % 2 == 1 && nums[mid] == nums[mid-1]) || (mid % 2 == 0 && nums[mid] != nums[mid-1]))
                l = mid + 1;
            else
                r = mid - 1;
        }
        return 0;
    }
}
```
**Appendix**
---
The time complexity of binary search is O(log n).
Observe the data characteristics.