# Number of Islands
---
- ## Question:
> Given an m x n 2D binary grid grid which represents a map of '1's (land) and '0's (water), return the number of islands.
> 
> An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.
---
- ## Example:
> Input: grid = [
> 
> ["1","1","1","1","0"],
> 
> ["1","1","0","1","0"],
> 
> ["1","1","0","0","0"],
> 
> ["0","0","0","0","0"]
> 
> ]
> 
> Output: 1
---
- ## Solution:
**Code :**
```java
class Solution {
    public int numIslands(char[][] grid) {
        int count=0;
        for(int i=0;i<grid.length;i++)
        {
            for(int j=0;j<grid[0].length;j++)
            {
                if(grid[i][j]=='1')
                {
                    dfsFill(grid,i,j);
                    count++;
                }      
            }
        }   
        return count;
    }
    public void dfsFill(char[][] grid,int i,int j)
    {
        if(i>=0 && j>=0 && i<grid.length && j<grid[0].length && grid[i][j]=='1')
        {
            grid[i][j]='0';
            dfsFill(grid,i+1,j);
            dfsFill(grid,i-1,j);
            dfsFill(grid,i,j+1);
            dfsFill(grid,i,j-1);
        }
    }
}
