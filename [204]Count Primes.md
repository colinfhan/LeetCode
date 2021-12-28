**Number Theory**  
---
**Basic idea**  
Prime Number

Implementation
---
```java
class Solution {
    public int countPrimes(int n) {
        if (n<2)
            return 0;
        boolean[] prime = new boolean[n];
        int count = n - 2;
        for (int i = 2; i < n; ++i) {
            for (int j = 2; j * i < n; ++j) {
                if (!prime[j*i]) {
                    prime[j*i] = true;
                    --count;
                }
            }
        }
        return count;
    }
}
```
**Appendix**
---
None.