**Sorting**  
---
**Basic idea**  
Bucket sorting.

Implementation
---
```java
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        Map<Integer, Integer> bucket = new HashMap<Integer, Integer>();
        int[] ret = new int[k];
        for (int i:nums) {
            if (!bucket.containsKey(i))
                bucket.put(i, 1);
            else
                bucket.put(i, bucket.get(i)+1);
        }
        for (int i = 0; i < k; i++) {
            var ks = bucket.keySet();
            int max = -1;
            int maxk = -1;
            for(var j:ks) {
                if (bucket.get(j) > max) {
                    max = bucket.get(j);
                    maxk = j;
                }
            }
            bucket.remove(maxk);
            ret[i] = maxk;
        }
        return ret;
    }
}
```
**Appendix**
---
None.