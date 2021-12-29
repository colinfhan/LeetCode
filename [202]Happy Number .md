**Math**  
---
**Basic idea**  
Math

Implementation
---
```java
class Solution {
    public boolean isHappy(int n) {
        Set<Integer> set = new HashSet<>();
        while (true) {
            n = findNext(n);
            if (n == 1)
                return true;
            if (set.contains(n))
                return false;
            set.add(n);
        }
    }

    public int findNext(int n) {
        int sum = 0;
        while (n != 0) {
            sum += (n % 10) * (n % 10);
            n /= 10;
        }
        return sum;
    }
}
```
**Appendix**
---
None.