**Strings**  
---
**Basic idea**  
Palindrome string

Implementation
---
```java
class Solution {
    public int countBinarySubstrings(String s) {
        int ret = 0, pre = 0, cur = 0;
        char[] chars = s.toCharArray();
        char pt = '2';
        for (int i = 0; i < chars.length; ++i) {
            if (chars[i] != pt) {
                ret += Math.min(pre, cur);
                pre = cur;
                cur = 1;
                pt = chars[i];
            } else {
                cur++;
            }
        }
        ret += Math.min(pre, cur);
        return ret;
    }
}
```
**Appendix**
---
None.