**Linked List**  
---
**Basic idea**  
Merge linked list.

Implementation
---
```java
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode ret = new ListNode();
        ListNode cur = ret;
        while (list1 != null || list2 != null) {
            if (list1 == null) {
                cur.next = list2;
                break;
            } else if (list2 == null) {
                cur.next = list1;
                break;
            } else if (list1.val < list2.val) {
                cur.next = new ListNode(list1.val);
                cur = cur.next;
                list1 = list1.next;
            } else {
                cur.next = new ListNode(list2.val);
                cur = cur.next;
                list2 = list2.next;
            }
        }
        return ret.next;
    }
}
```
**Appendix**
---
None.