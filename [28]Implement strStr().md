**Strings**  
---
**Basic idea**  
Find sub-string.

Implementation
---
```java
class Solution {
    public int strStr(String haystack, String needle) {
        int i = 0, j = 0, pos = -1;
        while (true) {
            if (haystack.charAt(i++) == needle.charAt(j++)) {
                if (j == needle.length()) {
                    pos = i - j;
                    break;
                }
            }
            else {
                i = i - j + 1;
                j = 0;
            }
            if (i == haystack.length())
                break;
        }
        return pos;
    }
}
```
**Appendix**
---
None.