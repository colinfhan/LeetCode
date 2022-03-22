**Data Structure**  
---
**Basic idea**  
Hash Table

Implementation
---
```java
class Solution {
    public int longestConsecutive(int[] nums) {
        HashSet<Integer> hashSet = new HashSet<>();
        int ret = 0;
        for (int i = 0; i < nums.length; ++i) {
            hashSet.add(nums[i]);
        }
        while (!hashSet.isEmpty()) {
            int c = hashSet.iterator().next();
            int r = 1, h = c + 1, l = c - 1;
            hashSet.remove(c);
            while (hashSet.contains(h)) {
                r++;
                hashSet.remove(h++);
            }
            while (hashSet.contains(l)) {
                r++;
                hashSet.remove(l--);
            }
            ret = r > ret ? r : ret;
        }
        return ret;
    }
}
```
**Appendix**
---
None.