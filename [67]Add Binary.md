**Math**  
---
**Basic idea**  
Math

Implementation
---
```java
class Solution {
    public String addBinary(String a, String b) {
        StringBuilder n1 = new StringBuilder(a), n2 = new StringBuilder(b), ret = new StringBuilder();
        n1.reverse();
        n2.reverse();
        int len1 = n1.length(), len2 = n2.length(), p = 0, more = 0;
        while (p<len1 && p<len2) {
            int x = n1.charAt(p) - '0', y = n2.charAt(p) - '0';
            int res = x + y + more;
            ret.append(res % 2);
            more = res > 1 ? 1 : 0;
            ++p;
        }
        if (len1 == len2) {
            if (more == 1)
                ret.append(more);
        }
        else if (len1 > len2) {
            while (p < len1) {
                int x = n1.charAt(p++) - '0';
                int res = x + more;
                ret.append(res % 2);
                more = res > 1 ? 1 : 0;
            }
            if (more == 1)
                ret.append(more);
        }
        else {
            while (p < len2) {
                int x = n2.charAt(p++) - '0';
                int res = x + more;
                ret.append(res % 2);
                more = res > 1 ? 1 : 0;
            }
            if (more == 1)
                ret.append(more);
        }
        return ret.reverse().toString();
    }
}
```
**Appendix**
---
swap(ret, i, i + (int)Math.floor(Math.random()*1000) % (n - i)).