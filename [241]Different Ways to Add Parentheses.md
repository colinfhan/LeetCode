**Partitioning Algorithm**  
---
**Basic idea**  
Partitioning algorithm: Decomposition->Resolution->Merge.  
Decompose left and right with operators, distribute the solution, and perform merging.  

Implementation
---
```java
class Solution {
    public List<Integer> diffWaysToCompute(String expression) {
        List<Integer> ret = new ArrayList<>();
        for (int i = 0; i < expression.length(); ++i) {
            char c = expression.charAt(i);
            if (c == '+' || c == '-' || c == '*') {
                List<Integer> left = diffWaysToCompute(expression.substring(0, i));
                List<Integer> right = diffWaysToCompute(expression.substring(i + 1));
                for (int l : left)
                    for (int r : right)
                        ret.add(switch (c) {
                            case '+' -> l + r;
                            case '-' -> l - r;
                            default -> l * r;
                        });
            }
        }
        if (ret.isEmpty())
            ret.add(Integer.parseInt(expression));
        return ret;
    }
}
```
**Appendix**
---
None.