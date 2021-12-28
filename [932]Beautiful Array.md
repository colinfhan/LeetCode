**Partitioning Algorithm**  
---
**Basic idea**  
Partitioning algorithm.  

Implementation
---
```java
class Solution {
    public int[] beautifulArray(int n) {
        List<Integer> ret = new ArrayList<>();
        for (int i = 0; i < n; ++i) {
            ret.add(i+1);
        }
        exchange(ret, 0, n-1);
        return ret.stream().mapToInt(Integer::valueOf).toArray();
    }

    public void exchange(List<Integer> n, int s, int e) {
        if (s >= e)
            return;
        int pointer = s;
        for (int i = s; i <= e; ++i) {
            if ((i-s) % 2 == 0) {
                int t = n.get(i);
                n.remove(i);
                n.add(pointer++, t);
            }
        }
        exchange(n, s, (e-s)/2 + s);
        exchange(n, (e-s)/2 + s + 1, e);
    }
}
```
**Appendix**
---
None.