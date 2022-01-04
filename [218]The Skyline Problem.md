**Data Structure**  
---
**Basic idea**  
Priority Queue

Implementation
---
```java
class Solution {
    public List<List<Integer>> getSkyline(int[][] buildings) {
        List<List<Integer>> ret = new ArrayList<>();
        List<int[]> pointList = new ArrayList<>();
        for (int[] building : buildings) {
            int x1 = building[0], x2 = building[1], height = building[2];
            pointList.add(new int[]{x1, -height});
            pointList.add(new int[]{x2, height});
        }
        Collections.sort(pointList, (a, b) -> a[0] != b[0] ? Integer.compare(a[0],b[0]) : Integer.compare(a[1],b[1]));
        PriorityQueue<Integer> priorityQueue = new PriorityQueue<>((a,b) -> Integer.compare(b,a));
        int pre = 0;
        priorityQueue.add(pre);
        for (int[] point : pointList) {
            int x = point[0], height = point[1];
            if (height < 0)
                priorityQueue.add(-height);
            else
                priorityQueue.remove(height);

            int current = priorityQueue.peek();
            if (current != pre) {
                List<Integer> retList = new ArrayList<>();
                retList.add(x);
                retList.add(current);
                ret.add(retList);
                pre = current;
            }
        }
        return ret;
    }
}
```
**Appendix**
---
None.