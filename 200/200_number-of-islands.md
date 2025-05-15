BFS
```C++
class Solution {
public:
    int numIslands(vector<vector<char>>& grid) {
        int m = grid.size(), n = grid[0].size();
        vector<int> dx = {1, 0, -1, 0}, dy = {0, 1, 0, -1};
        int num_islands = 0;
        vector<vector<bool>> visited(m, vector<bool>(n, false));
        for (int x = 0; x < m; x++) {
            for (int y = 0; y < n; y++) {
                if (visited[x][y] || grid[x][y] != '1') continue;
                num_islands++;
                queue<pair<int, int>> q;
                q.emplace(x, y);
                visited[x][y] = true;
                while (!q.empty()) {
                    auto [x, y] = q.front();
                    q.pop();
                    for (int dir = 0; dir < 4; dir++) {
                        int neighbor_x = x + dx[dir], neighbor_y = y + dy[dir];
                        if (neighbor_x < 0 || neighbor_x >= m || neighbor_y < 0 || neighbor_y >= n) continue;
                        if (visited[neighbor_x][neighbor_y] || grid[neighbor_x][neighbor_y] == '0') continue;
                        q.emplace(neighbor_x, neighbor_y);
                        visited[neighbor_x][neighbor_y] = true;
                    }
                }
            }
        }
        return num_islands;
    }
};
```

DFS
```C++
class Solution {
    vector<int> dx = {1, 0, -1, 0}, dy = {0, 1, 0, -1};
public:
    int numIslands(vector<vector<char>>& grid) {
        vector<vector<char>> copied_grid = grid;
        int m = copied_grid.size(), n = copied_grid[0].size();
        int num_islands = 0;
        for (int x = 0; x < m; x++) {
            for (int y = 0; y < n; y++) {
                if (copied_grid[x][y] == '0')
                    continue;
                traverse(copied_grid, x, y);
                num_islands++;
            }
        }
        return num_islands;
    }

    void traverse(vector<vector<char>>& grid, int x, int y) {
        int m = grid.size(), n = grid[0].size();
        if (x < 0 || x >= m || y < 0 || y >= n) return;
        if (grid[x][y] == '0') return;
        grid[x][y] = '0';
        for (int dir = 0; dir < 4; dir++)
            traverse(grid, x + dx[dir], y + dy[dir]);
    }
};
```
