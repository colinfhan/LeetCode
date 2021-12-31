**Data Structure**  
---
**Basic idea**  
Stack, Queue

Implementation
---
```java
class MyQueue {
    int[] data;
    int head, rear;
    public MyQueue() {
        data = new int[200];
        head = 0;
        rear = -1;
    }

    public void push(int x) {
        data[++rear] = x;
    }

    public int pop() {
        return data[head++];
    }

    public int peek() {
        return data[head];
    }

    public boolean empty() {
        return  head > rear;
    }
}
```
**Appendix**
---
None.