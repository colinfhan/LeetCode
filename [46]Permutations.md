**Searching**  
---
**Basic idea**  
Backtracing.

Implementation
---
```java
class Solution {
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> ret = new ArrayList<>();
        backtracing(nums, 0, ret);
        return ret;
    }

    public void backtracing(int[] nums, int pos, List<List<Integer>> ret) {
        if (pos == nums.length - 1) {
            ret.add(Arrays.stream(nums).boxed().collect(Collectors.toList()));
            return;
        }

        for (int i = pos; i < nums.length; ++i) {
            swapArray(nums, i, pos);
            backtracing(nums, pos + 1, ret);
            swapArray(nums, i, pos);
        }

    }

    public void swapArray(int[] array, int x, int y) {
        int t = array[x];
        array[x] = array[y];
        array[y] = t;
    }
}
```
**Appendix**
---
None.