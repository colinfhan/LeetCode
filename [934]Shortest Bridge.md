**Searching**  
---
**Basic idea**  
DFS+BFS.

Implementation
---
```java
class Solution {
    int[][] directions = new int[][]{{1, 0}, {0, -1}, {-1, 0}, {0, 1}};

    public int shortestBridge(int[][] grid) {
        int n = grid.length;
        boolean found = false;
        Queue<int[]> points = new LinkedList<>();
        for (int i = 0; i < n; ++i) {
            if (found)
                break;
            for (int j = 0; j < n; ++j) {
                if (grid[i][j] == 1) {
                    markLandA(grid, i, j, points);
                    found = true;
                    break;
                }
            }
        }

        int ret = -1;
        while (!points.isEmpty()) {
            ++ret;
            int currentSize = points.size();
            for (int i = 0; i < currentSize; ++i) {
                int[] current = points.poll();
                int r = current[0];
                int c = current[1];
                for (int j = 0; j < 4; ++j) {
                    int x = r + directions[j][0];
                    int y = c + directions[j][1];
                    if ((0<=x&&x< n) && (0<=y&&y< n) && (grid[x][y])!=2) {
                        if (grid[x][y]==1)
                            return ret;
                        else if (grid[x][y]==0) {
                            grid[x][y]=2;
                            points.offer(new int[]{x,y});
                        }
                    }
                }
            }
        }

        return ret;
    }

    public void markLandA(int[][] grid, int r, int c, Queue<int[]> points) {
        grid[r][c] = 2;
        points.offer(new int[]{r,c});
        for (int i = 0; i < 4; ++i) {
            int x = r + directions[i][0];
            int y = c + directions[i][1];
            int n = grid.length;
            if ((0<=x&&x< n) && (0<=y&&y< n) && (grid[x][y]==1))
                markLandA(grid,x,y, points);
        }
    }
}
```
**Appendix**
---
None.