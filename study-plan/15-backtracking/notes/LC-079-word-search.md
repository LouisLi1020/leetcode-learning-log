# LC 79 · Word Search

| 項目 | 內容 |
|------|------|
| Pattern | Backtrack |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Word Search](https://leetcode.com/problems/word-search/) |

**題意：** board 上是否存在與 word 匹配的路徑（四方向、同格不重複）。

**核心：** 逐格 DFS backtrack：匹配 word[idx] 則標記 `#` 走四向；回溯還原。

```java
public boolean exist(char[][] board, String word) {
    for (int i = 0; i < board.length; i++)
        for (int j = 0; j < board[0].length; j++)
            if (dfs(board, word, i, j, 0)) return true;
    return false;
}
boolean dfs(char[][] b, String w, int r, int c, int idx) {
    if (idx == w.length()) return true;
    if (r < 0 || c < 0 || r >= b.length || c >= b[0].length) return false;
    if (b[r][c] != w.charAt(idx)) return false;
    char tmp = b[r][c];
    b[r][c] = '#';
    boolean found = dfs(b, w, r + 1, c, idx + 1) || dfs(b, w, r - 1, c, idx + 1)
        || dfs(b, w, r, c + 1, idx + 1) || dfs(b, w, r, c - 1, idx + 1);
    b[r][c] = tmp;
    return found;
}
```

**複雜度：** O(mn·4^L) 時間，O(L) 空間。
