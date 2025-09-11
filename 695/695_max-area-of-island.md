BFS
```C++
class Solution {
public:
    int maxAreaOfIsland(vector<vector<int>>& grid) {
        int m = grid.size(), n = grid[0].size();
        vector<int> dx = {1, 0, -1, 0}, dy = {0, 1, 0, -1};
        int ans = 0;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == 0) continue;
                int size = 0;
                queue<pair<int, int>> q;
                q.emplace(i, j);
                grid[i][j] = 0;
                size++;
                while (!q.empty()) {
                    auto [x, y] = q.front();
                    q.pop();
                    for (int dir = 0; dir < 4; dir++) {
                        int nx = x + dx[dir], ny = y + dy[dir];
                        if (nx < 0 || nx >= m || ny < 0 || ny >= n) continue;
                        if (grid[nx][ny] == 0) continue;
                        q.emplace(nx, ny);
                        grid[nx][ny] = 0;
                        size++;
                    }
                }
                ans = max(ans, size);
            }
        }
        return ans;
    }
};
```
