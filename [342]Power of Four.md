**Bit Manipulation**  
---
**Basic idea**  
AND

Implementation
---
```java
class Solution {
    public boolean isPowerOfFour(int n) {
        double res = Math.log10(n) / Math.log10(4);
        return (int)res == res;
    }
}
```
bit manipulation
```java
class Solution {
    public boolean isPowerOfFour(int n) {
        return n > 0 && (n & (n-1)) == 0 && (n & Integer.parseInt("1010101010101010101010101010101", 2)) != 0;
    }
}
```
**Appendix**
---
.