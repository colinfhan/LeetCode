**Greedy**
---
**Basic idea**  
Solve using one traversal  
**First attempt**
---

```java
class Solution {
    public boolean canPlaceFlowers(int[] flowerbed, int n) {
        int count = 0;
        if (flowerbed.length == 1 && flowerbed[0] == 0)
            return 1>=n;
        if (flowerbed.length == 1 && flowerbed[0] == 1)
            return 0>=n;
        if (flowerbed[0] == 0 && flowerbed[1] == 0) {
            flowerbed[0] = 1;
            count++;
        }
        for (int i = 1; i < flowerbed.length - 1; i++) {
            if (flowerbed[i] == 0 && flowerbed[i-1] ==0 && flowerbed[i+1] ==0) {
                flowerbed[i] = 1;
                count++;
            }
        }
        if (flowerbed[flowerbed.length-2] == 0 && flowerbed[flowerbed.length-1] == 0) {
            flowerbed[flowerbed.length - 1] = 1;
            count++;
        }
        return count>=n;
    }
}
```

T <89.35%  
S <63.35%  
**Appendix**
---