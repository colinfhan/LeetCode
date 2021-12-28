**Math**  
---
**Basic idea**  
Math - Incremental conversion

Implementation
---
```java
class Solution {
    public String convertToTitle(int columnNumber) {
        StringBuilder sb = new StringBuilder();
        int rem, quo;
        while (columnNumber != 0) {
            --columnNumber;
            quo = columnNumber / 26;
            rem = columnNumber % 26;
            columnNumber = quo;
            sb.append((char)(rem + 'A'));
        }
        return sb.reverse().toString();
    }
}
```
**Appendix**
---
swap(ret, i, i + (int)Math.floor(Math.random()*1000) % (n - i)).