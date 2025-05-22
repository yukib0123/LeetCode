```C++
class Solution {
public:
    int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
        int m = obstacleGrid.size(), n = obstacleGrid[0].size();
        vector<vector<int>> count(m + 1, vector<int>(n + 1, 0));
        if (obstacleGrid[0][0] == 1) return 0;
        count[1][1] = 1;
        for (int x = 1; x <= m; x++) {
            for (int y = 1; y <= n; y++) {
                if (x == 1 && y == 1) continue;
                if (obstacleGrid[x - 1][y - 1] == 1) continue;
                count[x][y] = count[x - 1][y] + count[x][y - 1];
            } 
        }
        return count[m][n];
    }
};
```
