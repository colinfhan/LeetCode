**Two pointer**  
---
**Basic idea**  
Simple exercise.

Implementation
---
```java
class Solution {
    int c = 0;
    public boolean validPalindrome(String s) {
        char[] sArray = s.toCharArray();
        int l = 0;
        int r = sArray.length - 1;
        while (l < r) {
            if (sArray[l] == sArray[r]) {
                l++;
                r--;
            } else {
                if (c == 0) {
                    c++;
                    return validPalindrome(s.substring(l, r)) || validPalindrome(s.substring(l + 1, r + 1));
                }
                return false;
            }

        }
        return true;
    }
}
```
**Appendix**
---
Additional functions or global variables can be defined to assist in solving the problem.