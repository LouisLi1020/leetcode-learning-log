# LC 130 · Surrounded Regions

| 項目 | 內容 |
|------|------|
| Pattern | DFS from border |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Surrounded Regions](https://leetcode.com/problems/surrounded-regions/) |

**題意：** 把被 `'X'` 包圍的 `'O'` 翻成 `'X'`；邊界 `'O'` 及與之相連的不翻。

**核心：** 從四邊界 `'O'` 做 DFS 標記 `'#'`（安全區）；再掃描：`'O'`→`'X'`，`'#'`→`'O'`。

```java
public void solve(char[][] board) {
    int m = board.length, n = board[0].length;
    for (int i = 0; i < m; i++) { dfs(board, i, 0); dfs(board, i, n - 1); }
    for (int j = 0; j < n; j++) { dfs(board, 0, j); dfs(board, m - 1, j); }
    for (int i = 0; i < m; i++)
        for (int j = 0; j < n; j++) {
            if (board[i][j] == 'O') board[i][j] = 'X';
            else if (board[i][j] == '#') board[i][j] = 'O';
        }
}
void dfs(char[][] b, int r, int c) {
    if (r < 0 || c < 0 || r >= b.length || c >= b[0].length || b[r][c] != 'O') return;
    b[r][c] = '#';
    dfs(b, r + 1, c); dfs(b, r - 1, c); dfs(b, r, c + 1); dfs(b, r, c - 1);
}
```

**複雜度：** O(mn) 時間，O(mn) 空間。
