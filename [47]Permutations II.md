**Searching**  
---
**Basic idea**  
Backtracing.

Implementation
---
```java
class Solution {
    public List<List<Integer>> permuteUnique(int[] nums) {
        List<List<Integer>> ret = new ArrayList<>();
        findPermutations(nums, 0, ret);
        return ret;
    }

    public void findPermutations(int[] nums, int pos, List<List<Integer>> ret) {
        if (pos == nums.length - 1) {
            List<Integer> local = Arrays.stream(nums).boxed().collect(Collectors.toList());
            if (!ret.contains(local))
                ret.add(local);
            return;
        }
        for (int i = pos; i < nums.length; ++i) {
            swapArray(nums, pos, i);
            findPermutations(nums, pos + 1, ret);
            swapArray(nums, pos, i);
        }
    }

    public void swapArray(int[] array, int i, int j) {
        int t = array[i];
        array[i] = array[j];
        array[j] = t;
    }
}
```
**Appendix**
---
None.