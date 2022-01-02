**Data Structure**  
---
**Basic idea**  
Stack

Implementation
---
A brute-force approach.
```java
class Solution {
    public int[] dailyTemperatures(int[] temperatures) {
        int[] ret = new int[temperatures.length];
        int point, count;
        for (int i = 0; i < temperatures.length; ++i) {
            point = temperatures[i];
            count = 0;
            for (int j = i + 1; j < temperatures.length; ++j) {
                if (temperatures[j] > point) {
                    ret[i] = ++count;
                    break;
                }
                else
                    ++count;
            }
        }
        return ret;
    }
}
```
Monotonic Stack
```java
class Solution {
    public int[] dailyTemperatures(int[] temperatures) {
        Stack<Integer> stack = new Stack<>();
        int[] ret = new int[temperatures.length];
        for (int i = 0; i < temperatures.length; ++i) {
            while (!stack.isEmpty() && temperatures[i] > temperatures[stack.peek()]) {
                int date = stack.pop();
                ret[date] = i - date;
            }
            stack.push(i);
        }
        return ret;
    }
}
```
**Appendix**
---
None.