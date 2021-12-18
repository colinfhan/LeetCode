**Searching**  
---
**Basic idea**  
BFS

Implementation
---
```java
class Solution {
    public List<Integer> findMinHeightTrees(int n, int[][] edges) {
        int min = n-1;
        List<Integer> ret = new ArrayList<>();
        for (int i = 0; i < n; ++i) {
            boolean[] visited = new boolean[edges.length];
            Arrays.fill(visited, false);
            Queue<Integer> currentPoint = new LinkedList<>();
            currentPoint.add(i);
            int current = scaleTree(edges, currentPoint, visited, min);
            if (current == min)
                ret.add(i);
            if (current < min) {
                min = current;
                ret.clear();
                ret.add(i);
            }
        }
        return ret;
    }

    public int scaleTree(int[][] edges, Queue<Integer> currentPoint, boolean[] visited, int max) {
        int round = 0;
        int left = edges.length;
        while (left>0) {
            int length = currentPoint.size();
            for (int i = 0; i < length; ++i) {
                int p = currentPoint.poll();
                for (int j = 0; j < edges.length; ++j) {
                    if (!visited[j]&&(edges[j][0]==p||edges[j][1]==p)){
                        int c = edges[j][0]==p?edges[j][1]:edges[j][0];
                        currentPoint.offer(c);
                        visited[j]=true;
                        --left;
                    }
                }
            }
            ++round;
            if (round>max)
                return round;
        }
        return round;
    }
}
```
Optimization
```java
class Solution {
    public List<Integer> findMinHeightTrees(int n, int[][] edges) {
        List<Integer> res = new ArrayList<>();
        if (n == 1) {
            res.add(0);
            return res;
        }
        int[] degree = new int[n];
        List<List<Integer>> map = new ArrayList<>();
        for (int i = 0; i < n; i++) {
            map.add(new ArrayList<>());
        }
        for (int[] edge : edges) {
            degree[edge[0]]++;
            degree[edge[1]]++;
            map.get(edge[0]).add(edge[1]);
            map.get(edge[1]).add(edge[0]);
        }
        Queue<Integer> queue = new LinkedList<>();
        for (int i = 0; i < n; i++) {
            if (degree[i] == 1) queue.offer(i);
        }
        while (!queue.isEmpty()) {
            res = new ArrayList<>();
            int size = queue.size();
            for (int i = 0; i < size; i++) {
                int cur = queue.poll();
                res.add(cur);
                List<Integer> neighbors = map.get(cur);
                for (int neighbor : neighbors) {
                    degree[neighbor]--;
                    if (degree[neighbor] == 1) {
                        queue.offer(neighbor);
                    }
                }
            }
        }
        return res;
    }
}
```
**Appendix**
---
None.