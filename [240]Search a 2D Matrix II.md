**Data Structure**  
---
**Basic idea**  
Array

Implementation
---
```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int m = matrix.length, n = matrix[0].length;
        for (int i = 0; i < m; ++i) {
            if (target < matrix[i][0] || target > matrix[i][n-1])
                continue;
            if (Arrays.binarySearch(matrix[i], target) >= 0)
                return true;
        }
        return false;
    }
}
```
Z-search
```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int m = matrix.length, n = matrix[0].length, x = 0, y = n - 1;
        while (x < m && y >= 0) {
            if (matrix[x][y] == target)
                return true;
            else if (matrix[x][y] > target)
                --y;
            else
                ++x;
        }
        return false;
    }
}
```
**Appendix**
---
None.