**Searching**  
---
**Basic idea**  
Backtracing.

Implementation
---
```java
class Solution {
    public List<List<Integer>> combine(int n, int k) {
        List<List<Integer>> ret = new ArrayList<>();
        int[] box = new int[k];
        Arrays.fill(box, 0);
        int[] pbox = {0};
        backtracking(n, k, box, pbox, 1, ret);
        return ret;
    }

    public void backtracking(int n, int k, int[] box, int[] pbox, int order, List<List<Integer>> ret) {
        if (pbox[0] == box.length) {
            ret.add(Arrays.stream(box).boxed().collect(Collectors.toList()));
            return;
        }
        for (int i = order; i <= n; ++i) {
            box[pbox[0]] = i;
            pbox[0]+=1;
            backtracking(n, k, box, pbox, i+1, ret);
            pbox[0]-=1;
        }
    }
}
```
**Appendix**
---
In backtracking algorithms, permutation problems are generally solved by swapping positions, and combination problems are generally solved by moving numbers into/out of sets.