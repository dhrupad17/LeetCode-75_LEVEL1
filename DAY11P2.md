# Unique Paths
---
- ## Question:
> There is a robot on an m x n grid. The robot is initially located at the top-left corner (i.e., grid[0][0]). The robot tries to move to the bottom-right corner (i.e., grid[m - 1][n - 1]). The robot can only move either down or right at any point in time.
> 
> Given the two integers m and n, return the number of possible unique paths that the robot can take to reach the bottom-right corner.
> 
> The test cases are generated so that the answer will be less than or equal to 2 * 109.
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2018/10/22/robot_maze.png)
> Input: m = 3, n = 7
> 
> Output: 28
---
- ## Solution:
**Code :**
```java
class Solution {
    public int uniquePaths(int m, int n) {
        if(m==1||n==1)
            return 1;
        m--;
        n--;
        long res=1;
        if(m<n)
        {
            m=m+n;
            n=m-n;
            m=m-n;
        }
        int j=1;
        for(int i=m+1;i<=m+n;i++,j++)
        {
            res=res*i;
            res=res/j;
        }
        return (int)res;
            
    }
}
