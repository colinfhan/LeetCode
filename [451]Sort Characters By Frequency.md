**Sorting**  
---
**Basic idea**  
Bucket sorting.

Implementation
---
```java
class Solution {
    public String frequencySort(String s) {
        Map<Character, Integer> maps = new HashMap<Character, Integer>();
        int m_f = 0;
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            int f = maps.getOrDefault(c, 0) + 1;
            maps.put(c, f);
            m_f = Math.max(m_f, f);
        }

        StringBuffer[] sb = new StringBuffer[m_f + 1];
        for (int i=0; i < sb.length; i++)
            sb[i] = new StringBuffer();
        for(var k:maps.keySet())
            sb[maps.get(k)].append(k);

        StringBuffer ret = new StringBuffer();
        for (int i = m_f; i > 0; --i) {
            for (int j=0; j<sb[i].length(); j++) {
                char ins = sb[i].charAt(j);
                ret.append(sb[i].substring(j, j+1).repeat(i));
            }
        }

        return ret.toString();
    }
}
```
**Appendix**
---
None.