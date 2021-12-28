**Math**  
---
**Basic idea**  
Math - Random

Implementation
---
```java
class Solution {
    int[] a;
    public Solution(int[] nums) {
        a = nums;
    }

    public int[] reset() {
        return a;
    }

    public int[] shuffle() {
        int[] ret = a.clone();
        int n = ret.length;
        for (int i = 0; i < n; ++i) {
            swap(ret, i, i + (int)Math.floor(Math.random()*1000) % (n - i));
        }
        return ret;
    }

    public void swap(int[] array, int p1, int p2) {
        int t = array[p1];
        array[p1] = array[p2];
        array[p2] = t;
    }
}
```
**Appendix**
---
swap(ret, i, i + (int)Math.floor(Math.random()*1000) % (n - i)).