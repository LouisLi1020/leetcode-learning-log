# LC 289 · Game of Life

| 項目 | 內容 |
|------|------|
| Pattern | Simulation |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Game of Life](https://leetcode.com/problems/game-of-life/) |

**題意：** 細胞生死依鄰居數量同步更新（原地、O(mn)）。

**核心：** 用 **第二狀態位** 編碼下一狀態；最後右移還原。

```java
public void gameOfLife(int[][] board) {
    int m = board.length, n = board[0].length;
    int[][] dirs = {{0,1},{0,-1},{1,0},{-1,0},{1,1},{1,-1},{-1,1},{-1,-1}};
    for (int i = 0; i < m; i++) {
        for (int j = 0; j < n; j++) {
            int live = 0;
            for (int[] d : dirs) {
                int ni = i + d[0], nj = j + d[1];
                if (ni >= 0 && ni < m && nj >= 0 && nj < n && Math.abs(board[ni][nj]) == 1)
                    live++;
            }
            if (board[i][j] == 1 && (live < 2 || live > 3)) board[i][j] = -1;
            if (board[i][j] == 0 && live == 3) board[i][j] = 2;
        }
    }
    for (int i = 0; i < m; i++)
        for (int j = 0; j < n; j++)
            if (board[i][j] > 0) board[i][j] = 1; else board[i][j] = 0;
}
```

**複雜度：** 時間 O(mn) · 空間 O(1)
