```C++
class Solution {
public:
    int uniquePaths(int m, int n) {
        vector<vector<int>> grid(m + 1, vector<int> (n + 1, 0));
        grid[1][1] = 1;
        for (int x = 1; x <= m; x++) {
            for (int y = 1; y <= n; y++) {
                if (x == 1 && y == 1) continue;
                grid[x][y] = grid[x-1][y] + grid[x][y-1];
            }
        }
        return grid[m][n];
    }
};
```
