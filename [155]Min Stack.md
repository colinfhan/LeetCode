**Data Structure**  
---
**Basic idea**  
Stack, Queue

Implementation
---
```java
class MinStack {
    Stack<Integer> stack, minValue;
    public MinStack() {
        stack = new Stack<>();
        minValue = new Stack<>();
    }

    public void push(int val) {
        stack.push(val);
        if (minValue.isEmpty() || val <= minValue.peek()) {
            minValue.push(val);
        }
    }

    public void pop() {
        int t = stack.pop();
        if (t == minValue.peek())
            minValue.pop();
    }

    public int top() {
        return stack.peek();
    }

    public int getMin() {
        return minValue.peek();
    }
}
```
**Appendix**
---
None.