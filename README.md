# LC-Python33
Dynamic planning 2


## 
July 06, 2023  4h

Congratulations!\
This is the 33th day for leetcode python study. Today we will learn about the Dynamic planning!\
The challenges today are especially about unique pathes to a destination. 


## 62.Unique Paths
```python
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        #create a two dimension array to store the result
        dp = [[0]*n for _ in range(m)]
        #initialize for the first column and first row
        for i in range(m):
            dp[i][0] = 1
        for j in range(n):
            dp[0][j] = 1
        #calculate the number of pathes for each grid
        for i in range(1, m):
            for j in range(1, n):
                dp[i][j] = dp[i-1][j] + dp[i][j-1]

        return dp[m-1][n-1]
```


## 63.Unique Paths II
```python
class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid: List[List[int]]) -> int:
        m = len(obstacleGrid)        #get the shape of the grid
        n = len(obstacleGrid[0])
        if obstacleGrid[m - 1][n - 1] == 1 or obstacleGrid[0][0] == 1:
            return 0
        dp = [[0] * n for _ in range(m)]
        for i in range(m):
            if obstacleGrid[i][0] == 0:  
                dp[i][0] = 1         #initialize the beganning grid in the ith row head
            else:
                break                #if meet the obstacle, end the loop, and the following ways are all 0, no way to get through
        for j in range(n):
            if obstacleGrid[0][j] == 0:
                dp[0][j] = 1         #initialize the beganning grid in the jth column head
            else:
                break
        for i in range(1, m):
            for j in range(1, n):
                if obstacleGrid[i][j] == 1:
                    continue
                dp[i][j] = dp[i - 1][j] + dp[i][j - 1]
        return dp[m - 1][n - 1]
```









