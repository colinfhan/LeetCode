**Data Structure**  
---
**Basic idea**  
Hash Table

Implementation
---
```java
class Solution {
    public int maxPoints(int[][] points) {
        HashMap<Double, Integer> hashMap = new HashMap<>();
        int ret = 1;
        for (int i = 0; i < points.length; ++i) {
            for (int j = i+1; j < points.length; ++j) {
                double k = points[j][1] - points[i][1] == 0 ? 0 : points[j][0] - points[i][0] == 0 ? Double.MAX_VALUE : (double) (points[j][1] - points[i][1]) / (points[j][0] - points[i][0]);
                hashMap.put(k, hashMap.getOrDefault(k, 1) + 1);
            }
            for (double key:hashMap.keySet())
                ret = Math.max(ret, hashMap.get(key));
            hashMap.clear();
        }
        return ret;
    }
}
```
**Appendix**
---
None.