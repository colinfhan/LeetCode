**Strings**  
---
**Basic idea**  
Substring.

Implementation
---
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        HashSet<Character> currentSet = new HashSet<>();
        int l = 0, r = 0, ret = 0;
        while (true) {
            if (r >= s.length())
                break;
            if (!currentSet.contains(s.charAt(r))) {
                ret = Math.max(ret, r - l + 1);
                currentSet.add(s.charAt(r));
                r++;
            }
            else {
                currentSet.remove(s.charAt(l));
                l++;
            }
        }
        return ret;
    }
}
```
**Appendix**
---
None.