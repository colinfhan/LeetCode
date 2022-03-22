**Data Structure**  
---
**Basic idea**  
Deque

Implementation
---
```java
class Solution {
    public int[] maxSlidingWindow(int[] nums, int k) {
        int[] ret = new int[nums.length - k + 1];
        Deque<Integer> deque = new ArrayDeque<>();
        int l = 0, r = 0;
        while (r < nums.length){
            while ((!deque.isEmpty()) && nums[r] > nums[deque.peekLast()])
                deque.pollLast();
            deque.addLast(r);
            if (deque.peekFirst() < l)
                deque.pollFirst();
            if (r - l + 1 >= k)
                ret[l++] = nums[deque.peekFirst()];
            r++;
        }
        return ret;
    }
}
```
**Appendix**
---
None.