**Bit Manipulation**  
---
**Basic idea**  
Application of Iso-or

Implementation
---
```java
class Solution {
    public int hammingDistance(int x, int y) {
        int count = 0;
        String bin = Integer.toBinaryString(x ^ y);
        for(char i:bin.toCharArray()) {
            if (i == '1')
                ++count;
        }
        return count;
    }
}
```
**Appendix**
---
None.