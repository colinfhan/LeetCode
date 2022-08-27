**Strings**  
---
**Basic idea**  
Palindromic Substring.

Implementation
---
```java
class Solution {
    public String longestPalindrome(String s) {
        String ret = "";
        for (int i = 0; i < s.length(); i++) {
            String s1 = findPalindrome(s, i, i);
            String s2 = findPalindrome(s, i, i+1);
            ret = ret.length() >= s1.length() ? ret : s1;
            ret = ret.length() >= s2.length() ? ret : s2;
        }
        return ret;
    }

    private String findPalindrome(String s, int l, int r) {
        if (l < 0 || r >= s.length() || (l >= 0 && r <= s.length() - 1 && s.charAt(l) != s.charAt(r)))
            return "";

        while (l > 0 && r < s.length() - 1) {
            if (s.charAt(l-1) == s.charAt(r+1)) {
                l--;
                r++;
            }
            else
                break;
        }

        return s.substring(l, r + 1);
    }
}
```
**Appendix**
---
None.