**Math**  
---
**Basic idea**  
Simulation

Implementation
---
```java
class Solution {
    public String addStrings(String num1, String num2) {
        StringBuilder ns1 = new StringBuilder(num1).reverse();
        StringBuilder ns2 = new StringBuilder(num2).reverse();
        StringBuilder ret = new StringBuilder();
        int m = num1.length(), n = num2.length();
        int s = Math.min(m, n);
        int more = 0, res = 0;
        int i = 0;
        for (; i < s; ++i) {
            res = ns1.charAt(i) - '0' + ns2.charAt(i) - '0';
            res += more;
            more = res / 10;
            res %= 10;
            ret.append(res);
        }
        if (m == n) {
            if (more == 1)
                ret.append(more);
        }
        else {
            if (m > n) {
                for (; i < m; ++i) {
                    res = ns1.charAt(i) - '0' + more;
                    more = res / 10;
                    res %= 10;
                    ret.append(res);
                }
            }
            else {
                for (; i < n; ++i) {
                    res = ns2.charAt(i) - '0' + more;
                    more = res / 10;
                    res %= 10;
                    ret.append(res);
                }
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
None.