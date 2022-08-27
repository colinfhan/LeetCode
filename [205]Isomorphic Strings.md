**Strings**  
---
**Basic idea**  
Hash table

Implementation
---
```java
class Solution {
    public boolean isIsomorphic(String s, String t) {
        int[] record1 = new int[128], record2 = new int[128];
        char[] chars1 = s.toCharArray(), chars2 = t.toCharArray();
        for (int i = 0; i < chars1.length; i++) {
            if (record1[chars1[i]] != record2[chars2[i]])
                return false;
            record1[chars1[i]] = record2[chars2[i]] = i + 1;
        }
        return true;
    }
}
```
**Appendix**
---
Positions are also important.