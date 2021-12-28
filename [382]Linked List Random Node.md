**Math**  
---
**Basic idea**  
Math - Probability

Implementation
---
```java
class Solution {

    List<Integer> list;
    int n;
    public Solution(ListNode head) {
        list = new ArrayList<>();
        while (head!=null) {
            list.add(head.val);
            head = head.next;
        }
        n = list.size();
    }

    public int getRandom() {
        return list.get((int)(Math.random() * n));
    }
}
```
Reservoir sampling
```java
class Solution {

    ListNode list;
    Random random;
    public Solution(ListNode head) {
        list = head;
        random = new Random();
    }

    public int getRandom() {
        ListNode p = list;
        int count = 1, val = 0;
        while (p!=null) {
            if (random.nextInt(count)+1 == count)
                val = p.val;
            p = p.next;
            ++count;
        }
        return val;
    }
}
```
**Appendix**
---
swap(ret, i, i + (int)Math.floor(Math.random()*1000) % (n - i)).