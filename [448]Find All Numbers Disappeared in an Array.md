**Data Structure**  
---
**Basic idea**  
Array

Implementation
---
```java
class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        int[] rea = new int[nums.length];
        List<Integer> ret = new ArrayList<>();
        for (int i:nums)
            ++rea[i-1];
        for (int i = 0; i < rea.length; ++i) {
            if (rea[i] == 0)
                ret.add(i+1);
        }
        return ret;
    }
}
```
Reduce space complexity
```java
class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        List<Integer> ret = new ArrayList<>();
        int n = nums.length;
        for (int i:nums) {
            int p = Math.abs(i);
            if (nums[(p - 1)] > 0)
                nums[(p - 1)] *= -1;
        }
        for (int i = 0; i < n; ++i) {
            if (nums[i] > 0)
                ret.add(i+1);
        }
        return ret;
    }
}
```
**Appendix**
---
None.