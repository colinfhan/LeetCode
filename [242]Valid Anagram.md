**Strings**  
---
**Basic idea**  
Hash table

Implementation
---
```java
class Solution {
    public boolean isAnagram(String s, String t) {
        int[] count = new int[26];
        Arrays.fill(count, 0);
        char[] chars = s.toCharArray();
        for (char c:chars) {
            count[c-'a']++;
        }
        char[] chars1 = t.toCharArray();
        for (char c:chars1) {
            count[c-'a']--;
        }
        for (int i:count) {
            if (i != 0)
                return false;
        }
        return true;
    }
}
```
**Appendix**
---
There cannot be duplicate elements in a HashSet.