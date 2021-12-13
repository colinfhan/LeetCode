**Greedy**  
---
**Basic idea**  
Auxiliary data preparation  
Finding patterns: finding and locating segment by segment

**Implementation **
---
```java
class Solution {
    public List<Integer> partitionLabels(String s) {
        Map<Character, int[]> labelMap = new HashMap<Character, int[]>();
        for(int i=0;i<s.length();i++) {
            char c=s.charAt(i);
            if (!labelMap.containsKey(c))
                labelMap.put(c, new int[]{i,i});
            else
                labelMap.put(c, new int[]{labelMap.get(c)[0], i});
        }
        int start = 0;
        int end = 0;
        List<Integer> result = new ArrayList<>();
        for(int i=0;i<s.length();i++) {
            char c=s.charAt(i);
            end = Integer.max(end, labelMap.get(c)[1]);
            if (end == i) {
                result.add(end - start + 1);
                start = end + 1;
            }
        }
        return result;
    }
}
```
**Appendix**
---
Map<Character, int[]> labelMap = new HashMap<Character, int[]>()