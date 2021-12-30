**Bit Manipulation**  
---
**Basic idea**  
pattern

Implementation
---
```java
class Solution {
    public int findComplement(int num) {
        long total = 1;
        while (true) {
            if (num >= total) {
                total <<= 1;
            }
            else {
                return (int)(total - num - 1);
            }
        }
    }
}
```
**Appendix**
---
Find the pattern that input + output = 2^x - 1.