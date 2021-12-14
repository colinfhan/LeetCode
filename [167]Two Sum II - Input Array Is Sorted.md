**Two pointer**  
---
**Basic idea**  
Double Pointer Co-Finding

Implementation
---
```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        for (int i = 0; i < numbers.length; i++) {
            for (int j=i+1; j < numbers.length; j++)
                if (numbers[i]+numbers[j]==target)
                    return new int[]{i+1, j+1};
        }
        return new int[]{0,0};
    }
}
```
Noting that the input array is ordered, optimize the direction of pointer movement  
```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int b = 0;
        int e = numbers.length-1;
        while (b<e) {
            if (numbers[b] + numbers[e] > target)
                e--;
            if (numbers[b] + numbers[e] < target)
                b++;
            if (numbers[b] + numbers[e] == target)
                break;
        }
        return new int[]{b+1, e+1};
    }
}
```
**Appendix**
---
Optimize code to take advantage of known conditions.