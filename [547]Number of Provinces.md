**Searching**  
---
**Basic idea**  
DFS

Implementation
---
```java
class Solution {
    public int findCircleNum(int[][] isConnected) {
        int n = isConnected.length, count = 0;
        boolean[] notVisited = new boolean[n];
        Arrays.fill(notVisited, true);
        for (int i = 0; i < n; ++i) {
            if (notVisited[i]) {
                dfs(isConnected, i, notVisited);
                ++count;
            }
        }
        return count;
    }

    public void dfs(int[][] isConnected, int pos, boolean[] notVisited) {
        notVisited[pos] = false;
        for (int i = 0; i < isConnected.length; ++i) {
            if (isConnected[pos][i] == 1 && notVisited[i])
                dfs(isConnected, i, notVisited);
        }
    }
}
```



**Appendix**
---
None.