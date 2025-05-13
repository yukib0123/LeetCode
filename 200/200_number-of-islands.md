```C++
class Solution {
public:
    int numIslands(vector<vector<char>>& grid) {
        int m = grid.size(), n = grid[0].size();
        vector<int> dx = {1, 0, -1, 0}, dy = {0, 1, 0, -1};
        int ans = 0;
        vector<vector<bool>> visited(m, vector<bool>(n, false));
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                queue<pair<int, int>> q;
                if (!visited[i][j] && grid[i][j] == '1') {
                    ans++;
                    q.emplace(i, j);
                    visited[i][j] = true;
                    while (!q.empty()) {
                        auto [x, y] = q.front();
                        q.pop();
                        for (int dir = 0; dir < 4; dir++) {
                            int nx = x + dx[dir], ny = y + dy[dir];
                            if (nx < 0 || nx >= m || ny < 0 || ny >= n) continue;
                            if (!visited[nx][ny] && grid[nx][ny] == '1') {
                                q.emplace(nx, ny);
                                visited[nx][ny] = true;
                            }
                        }
                    }
                }
            }
        }
        return ans;
    }
};
```
