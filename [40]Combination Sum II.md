**Searching**  
---
**Basic idea**  
Backtracing.

Implementation
---
```java
class Solution {
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        Arrays.sort(candidates);
        List<List<Integer>> ret = new ArrayList<>();
        List<Integer> local = new ArrayList<>();
        findCombination(candidates, target, 0, local, ret, 0);
        return ret;
    }

    public void findCombination(int[] candidates, int target, int position, List<Integer> local, List<List<Integer>> ret, int sum) {
        if (sum > target)
            return;
        if (sum == target) {
            List<Integer> current = new ArrayList<Integer>(local);
            if (!ret.contains(current))
                ret.add(current);
            return;
        }
        for (int i = position; i < candidates.length; ++i) {
            local.add(candidates[i]);
            sum+=candidates[i];
            findCombination(candidates, target, i + 1, local, ret, sum);
            local.remove(local.size()-1);
            sum-=candidates[i];
        }
    }
}
```
Optimization time.
```java
class Solution {
    List<int[]> freq = new ArrayList<int[]>();
    List<List<Integer>> ans = new ArrayList<List<Integer>>();
    List<Integer> sequence = new ArrayList<Integer>();

    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        Arrays.sort(candidates);
        for (int num : candidates) {
            int size = freq.size();
            if (freq.isEmpty() || num != freq.get(size - 1)[0]) {
                freq.add(new int[]{num, 1});
            } else {
                ++freq.get(size - 1)[1];
            }
        }
        dfs(0, target);
        return ans;
    }

    public void dfs(int pos, int rest) {
        if (rest == 0) {
            ans.add(new ArrayList<Integer>(sequence));
            return;
        }
        if (pos == freq.size() || rest < freq.get(pos)[0]) {
            return;
        }

        dfs(pos + 1, rest);

        int most = Math.min(rest / freq.get(pos)[0], freq.get(pos)[1]);
        for (int i = 1; i <= most; ++i) {
            sequence.add(freq.get(pos)[0]);
            dfs(pos + 1, rest - i * freq.get(pos)[0]);
        }
        for (int i = 1; i <= most; ++i) {
            sequence.remove(sequence.size() - 1);
        }
    }
}
```
**Appendix**
---
None.