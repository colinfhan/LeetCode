**Two pointer**  
---
**Basic idea**  
Use Floyd's circle method.

Implementation
---
```java
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode fast = head;
        ListNode slow = head;
        do {
            if (fast == null || fast.next == null)
                return null;
            slow = slow.next;
            fast = fast.next.next;
        } while (fast != slow);
        fast = head;
        while (fast != slow) {
            slow = slow.next;
            fast = fast.next;
        }
        return fast;
    }
}
```
**Appendix**
---
Remember Floyd's circle method.