**Sorting**  
---
**Basic idea**  
This problem is the classic "Dutch flag problem", first proposed by computer scientist Edsger W. Dijkstra.

Implementation
---
```java
class Solution {
    public void sortColors(int[] nums) {
        Arrays.sort(nums);
    }
}
```
Without sort method, we can use two pointers to solve this problem.
```java
class Solution {
    public void sortColors(int[] nums) {
        int l = 0, r = nums.length - 1;
        for (int i = 0; i <= r; ++i) {
            while (nums[i]==2 && i<=r) {
                int t = nums[i];
                nums[i] = nums[r];
                nums[r] = t;
                --r;
            }
            if (nums[i]==0) {
                int t = nums[i];
                nums[i] = nums[l];
                nums[l] = t;
                ++l;
            }
        }
    }
}
```
**Appendix**
---
None.