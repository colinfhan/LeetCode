**Greedy**  
---
**Basic idea**  
Greedy

Implementation
---
```java
class Solution {
    public int wiggleMaxLength(int[] nums) {
        int n = nums.length;
        if ((n == 1) || (n == 2 && nums[0] == nums[1]))
            return 1;
        if (n == 2 && nums[0] != nums[1])
            return 2;
        int pointer = nums[1];
        boolean ss = nums[1] == nums[0];
        boolean upper = nums[1] > nums[0];
        int length = ss ? 1 : 2;
        for (int i = 2; i < n; ++i) {
            if ((upper && pointer > nums[i]) || (!upper && pointer < nums[i]) || ss) {
                ++length;
                if (ss) {
                    upper = pointer < nums[i];
                    if (pointer == nums[i])
                        --length;
                    else
                        ss = false;
                }
                else
                    upper = !upper;
            }
            pointer = nums[i];
        }
        return length;
    }
}
```
**Appendix**
---
None.