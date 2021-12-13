**Greedy**  
First Attempt
```java
class Solution {
    public int candy(int[] ratings) {
        int [] result = new int[ratings.length];
        for (int i = 0; i< result.length; i++)
            result[i] = 1;
        for (int i = 0; i < result.length - 1; i++)
            if (ratings[i] < ratings[i+1])
                result[i+1] = result[i] + 1;
        for (int i = result.length-1; i>0; i--)
            if (ratings[i-1]>ratings[i] && result[i-1]<=result[i])
                result[i-1] = result[i] + 1;
        int sum = 0;
        for (int i : result)
            sum += i;
        return sum;
    }
}
```
T <99.81%  
S <87.71%  
Optimize the initialization section
```java
class Solution {
    public int candy(int[] ratings) {
        int [] result = new int[ratings.length];
        Arrays.fill(result, 1);
        for (int i = 0; i < result.length - 1; i++)
            if (ratings[i] < ratings[i+1])
                result[i+1] = result[i] + 1;
        for (int i = result.length-1; i>0; i--)
            if (ratings[i-1]>ratings[i] && result[i-1]<=result[i])
                result[i-1] = result[i] + 1;
        int sum = 0;
        for (int i : result)
            sum += i;
        return sum;
    }
}
```
T <93.63%
S <99.43%