**Dynamic Planning**  
---
**Basic idea**  
init of DP

Implementation
---
Recursive implementation
```java
class Solution {
    public int climbStairs(int n) {
        return findAns(n);
    }

    public int findAns(int n) {
        if (n==1)
            return 1;
        if (n==2)
            return 2;
        return climbStairs(n-1) + climbStairs(n-2);
    }
}
```
Recursion with memo
```java
class Solution {
    int[] memo;
    public int climbStairs(int n) {
        if (n<3)
            return n;
        memo = new int[n+1];
        memo[1]=1;
        memo[2]=2;
        return findAns(n);
    }

    public int findAns(int n) {
        if (memo[n]>0)
            return memo[n];
        memo[n]=findAns(n-1) + findAns(n-2);
        return memo[n];
    }
}
```
Dynamic Planning
```java
class Solution {
    public int climbStairs(int n) {
        if (n<3)
            return n;
        int[] dp = new int[n+1];
        dp[1] = 1;
        dp[2] = 2;
        for (int i = 3; i <= n; ++i) {
            dp[i] = dp[i-1] + dp[i-2];
        }
        return dp[n];
    }
}
```
Optimizing space complexity
```java
class Solution {
    public int climbStairs(int n) {
        if (n<3)
            return n;
        int pre1 = 1;
        int pre2 = 2;
        int current = 3;
        for (int i = 3; i <= n; ++i) {
            current = pre2+pre1;
            pre1=pre2;
            pre2=current;
        }
        return current;
    }
}
```
**Appendix**
---
None.