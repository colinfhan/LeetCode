**Strings**  
---
**Basic idea**  
Palindrome string

Implementation
---
```java
class Solution {
    public int countSubstrings(String s) {
        int count = 0;
        for (int i = 0; i < s.length(); i++) {
            count += countCurrent(s, i, i);
            count += countCurrent(s, i, i+1);
        }
        return count;
    }

    private int countCurrent(String s, int l, int r) {
        int count = 0;
        while (true) {
            if (l >= 0 && r < s.length() && s.charAt(l--) == s.charAt(r++))
                count++;
            else break;
        }
        return count;
    }
}
```
**Appendix**
---
Center Extensions.