**Bitwise Operations**  
---
**Basic idea**  
Reverse

Implementation
---
```java
public class Solution {
    // you need treat n as an unsigned value
    public int reverseBits(int n) {
        String input = Integer.toBinaryString(n);
        StringBuilder sb = new StringBuilder("0".repeat(32-input.length()) + input);
        return (int)Long.parseLong(sb.reverse().toString(), 2);
    }
}
```
**Appendix**
---
None.