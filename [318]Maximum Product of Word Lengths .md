**Bit Manipulation**  
---
**Basic idea**  
Mask

Implementation
---
```java
class Solution {
    public int maxProduct(String[] words) {
        int max = 0, n = words.length;
        int[] mask = new int[n];
        for (int i = 0; i < n; ++i) {
            for(char c:words[i].toCharArray()) {
                mask[i] |= 1 << (c-'a');
            }
        }
        for (int i = 0; i < words.length - 1; ++i) {
            for (int j = i + 1; j < words.length; ++j) {
                if ((mask[i] & mask[j]) == 0)
                    max = Math.max(max, words[i].length() * words[j].length());
            }
        }
        return max;
    }
}
```
**Appendix**
---
None.