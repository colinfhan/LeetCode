**Data Structure**  
---
**Basic idea**  
Priority Queue

Implementation
---
```java
class Solution {
    public ListNode mergeKLists(ListNode[] lists) {
        PriorityQueue<Integer> integerPriorityQueue = new PriorityQueue<>();
        for (ListNode list : lists) {
            while (list != null) {
                integerPriorityQueue.add(list.val);
                list = list.next;
            }
        }
        ListNode ret, p;
        if (!integerPriorityQueue.isEmpty()) {
            ret = p = new ListNode(integerPriorityQueue.poll());
            while (!integerPriorityQueue.isEmpty()) {
                p.next = new ListNode(integerPriorityQueue.poll());
                p = p.next;
            }
        }
        else {
            return null;
        }
        return ret;
    }
}
```
**Appendix**
---
None.