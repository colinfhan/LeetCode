[Category]Greedy
First Attempt
```java
class Solution {
    public int findContentChildren(int[] g, int[] s) {
        Arrays.sort(g);
        Arrays.sort(s);
        int result = 0;
        int pointer = 0;
        for (int need:g) {
            while (true) {
                if (pointer >= s.length) {
                    return result;
                }
                if (s[pointer] >= need) {
                    result++;
                    pointer++;
                    break;
                } else {
                    pointer++;
                    if (pointer >= s.length)
                        return result;
                }
            }
        }
        return result;
    }
}
```
Try to use two pointers for streamlining
```java
class Solution {
    public int findContentChildren(int[] g, int[] s) {
        Arrays.sort(g);
        Arrays.sort(s);
        int pointer_child = 0, pointer_cookie = 0;
        while (pointer_child < g.length && pointer_cookie < s.length) {
            if (g[pointer_child] <= s[pointer_cookie])
                pointer_child++;
            pointer_cookie++;
        }
        return pointer_child;
    }
}
```
T>98.64
S>86.99