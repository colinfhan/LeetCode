**Searching**  
---
**Basic idea**  
DFS

Implementation
---
Stack version
```java
class Solution {
    public int maxAreaOfIsland(int[][] grid) {
        int[][] testDirection = new int[][] {{-1,0}, {0,1}, {1,0}, {0,-1}};
        int m = grid.length, n = grid[0].length, local, max = 0, x, y;
        for (int i = 0; i < m; ++i) {
            for (int j = 0; j < n; ++j) {
                if (grid[i][j] == 1) {
                    Stack<int[]> stack = new Stack<>();
                    grid[i][j] = 0;
                    stack.push(new int[]{i, j});
                    local = 1;
                    while (!stack.empty()) {
                        int[] currentLoc = stack.pop();
                        for (int k = 0; k < 4; ++k) {
                            x = currentLoc[0] + testDirection[k][0];
                            y = currentLoc[1] + testDirection[k][1];
                            if ((0<=x && x<m) && (0<=y && y<n) && grid[x][y] == 1) {
                                grid[x][y] = 0;
                                stack.push(new int[]{x,y});
                                local++;
                            }
                        }
                    }
                    max = Math.max(max, local);
                }
            }
        }
        return max;
    }
}
```
Without sort method, we can use two pointers to solve this problem.
```java
class Solution {
    public int maxAreaOfIsland(int[][] grid) {
        int max = 0;
        for (int i = 0; i < grid.length; ++i) {
            for (int j = 0; j < grid[0].length; ++j) {
                if (grid[i][j] == 1){
                    max = Math.max(max, dfs(grid, i, j));
                }
            }
        }
        return max;
    }

    public int dfs(int[][] grid,int a,int b) {
        if (grid[a][b] == 0)
            return 0;
        grid[a][b] = 0;
        int[][] testDirection = new int[][] {{-1,0}, {0,1}, {1,0}, {0,-1}};
        int x, y, local = 1;
        for (int i = 0; i < 4; ++i) {
            x = a + testDirection[i][0];
            y = b + testDirection[i][1];
            if ((0<=x && x<grid.length) && (0<=y && y<grid[0].length) && (grid[x][y]==1))
                local += dfs(grid, x, y);
        }
        return local;
    }
}
```
**Appendix**
---
None.