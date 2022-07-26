**Strings**  
---
**Basic idea**  
Palindrome.

Implementation
---
```java
class Solution {
    public int longestPalindrome(String s) {
        HashMap<Character, Integer> hashMap = new HashMap<>();
        for (char c : s.toCharArray()) {
            hashMap.put(c, hashMap.getOrDefault(c, 0) + 1);
        }

        boolean flag = true;
        int ret = 0;
        for (var es : hashMap.entrySet()) {
            int c = es.getValue();
            if (c % 2 == 1) {
                if (flag) {
                    ret += c;
                    flag = false;
                }
                else
                    ret += (c - 1);
            }
            else
                ret += c;
        }
        return ret;
    }
}
```
**Appendix**
---
None.