**Math**  
---
**Basic idea**  
Math - Rejected Sampling

Implementation
---
```java
class Solution extends SolBase {
    public int rand10() {
        int pos, a, b;
        do {
            a = rand7();
            b = rand7();
            pos = (a - 1) * 7 + b;
        } while(pos > 40);
        return (pos - 1) % 10 + 1;
    }
}
```
**Appendix**
---
None.