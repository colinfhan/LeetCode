**Bit Manipulation**  
---
**Basic idea**  
bm

Implementation
---
```java
class Solution {
    public boolean hasAlternatingBits(int n) {
        int rec = -1, mod;
        while (n!=0) {
            mod = n % 2;
            if ((mod==0 && rec==0) || (mod==1 && rec==1)) {
                return false;
            }
            rec = mod;
            n >>= 1;
        }
        return true;
    }
}
```
Another solution
```java
class Solution {
    public boolean hasAlternatingBits(int n) {
        return !(Integer.toBinaryString(n).contains("11") || Integer.toBinaryString(n).contains("00"));
    }
}
```
**Appendix**
---
None.