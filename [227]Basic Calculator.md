**Strings**  
---
**Basic idea**  
String

Implementation
---
```java
class Solution {
    public int calculate(String s) {
        List<int[]> record = new ArrayList<>();
        HashMap<Character, Integer> hashMap = new HashMap<>();
        hashMap.put('+', 0);hashMap.put('-', 1);hashMap.put('*', 2);hashMap.put('/', 3);
        int currentNumber = 0;
        int currentSymbol = -1;
        for (char c : ("+" + s).toCharArray()) {
            if (hashMap.containsKey(c)) {
                if (currentSymbol != -1) {
                    record.add(new int[]{currentSymbol, currentNumber});
                    currentNumber = 0;
                }
                currentSymbol = hashMap.get(c);
            }
            else if ('0' <= c && c <= '9')
                currentNumber = currentNumber * 10 + c - '0';
        }
        record.add(new int[]{currentSymbol, currentNumber});

        int pos1 = 0, pos2 = 0;
        for(int[] pair : record) {
            switch (pair[0]) {
                case 0 -> {
                    pos1 += pos2;
                    pos2 = pair[1];
                }
                case 1 -> {
                    pos1 += pos2;
                    pos2 = -pair[1];
                }
                case 2 -> pos2 *= pair[1];
                case 3 -> pos2 /= pair[1];
            }
        }

        return pos1 + pos2;
    }
}
```
**Appendix**
---
None.