**Two pointer**  
---
**Basic idea**  
Simulation.

Implementation
---
```java
class Solution {
    public String findLongestWord(String s, List<String> dictionary) {
        Collections.sort(dictionary, (s1, s2)->
                s1.length()!=s2.length()?Integer.compare(s2.length(), s1.length()):s1.compareTo(s2));
        for(String i:dictionary) {
            int ps = 0;
            int pi = 0;
            while (ps<s.length()) {
                if (i.charAt(pi) == s.charAt(ps)){
                    pi++;
                    ps++;
                } else {
                    ps++;
                }
                if (pi == i.length())
                    return i;
            }
        }
        return "";
    }
}
```
**Appendix**
---
The comparison of two collections is implemented by Collections.sort method.