**Searching**  
---
**Basic idea**  
DFS  
Traversing backwards from four edges can save time.  
Note the problem transformation.

Implementation
---
```java
class Solution {
    int[][] direction = new int[][]{{-1,0}, {0,1}, {1,0}, {0,-1}};
    public List<List<Integer>> pacificAtlantic(int[][] heights) {
        List<List<Integer>> ret = new ArrayList<>();
        int m = heights.length, n = heights[0].length;
        boolean[][] toPacific = new boolean[m][n], toAtlantic = new boolean[m][n];
        for (int i = 0; i < m; ++i) {
            Arrays.fill(toPacific[i], false);
            Arrays.fill(toAtlantic[i], false);
        }

        for (int i = 0; i < m; ++i) {
            dfs(heights, toPacific, i, 0);
            dfs(heights, toAtlantic, i, n-1);
        }

        for (int i = 0; i < n; ++i) {
            dfs(heights, toPacific, 0, i);
            dfs(heights, toAtlantic, m-1, i);
        }

        for (int i = 0; i < m; ++i) {
            for (int j = 0; j < n; ++j) {
                if (toPacific[i][j] && toAtlantic[i][j])
                    ret.add(Arrays.asList(i, j));
            }
        }

        return ret;
    }

    public void dfs(int[][] heights, boolean[][] toOcean, int r, int c) {
        if (toOcean[r][c])
            return;
        toOcean[r][c] = true;
        for (int i = 0; i < 4; ++i) {
            int x = r + direction[i][0];
            int y = c + direction[i][1];
            if ((0<=x && x<heights.length) && (0<=y && y<heights[0].length) && (heights[r][c]<=heights[x][y]))
                dfs(heights, toOcean, x, y);
        }
    }
}
```
**Appendix**
---
None.