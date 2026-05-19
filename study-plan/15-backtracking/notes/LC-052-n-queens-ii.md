# LC 52 · N-Queens II

| 項目 | 內容 |
|------|------|
| Pattern | Backtrack |
| 難度 | Hard |
| 狀態 | **done** |
| 題目 | [N-Queens II](https://leetcode.com/problems/n-queens-ii/) |

**題意：** n×n 棋盤放 n 皇后，求不同解法總數（不能同列、同對角）。

**核心：** 逐行放皇后；用 col、diag1(r+c)、diag2(r-c+n) 三 set O(1) 判突。

| 集合 | 表示 |
|------|------|
| cols | 已占欄 |
| d1 | r+c 主對角 |
| d2 | r-c 副對角 |

```java
int count = 0;

public int totalNQueens(int n) {
    backtrack(n, 0, new HashSet<>(), new HashSet<>(), new HashSet<>());
    return count;
}
void backtrack(int n, int r, Set<Integer> cols, Set<Integer> d1, Set<Integer> d2) {
    if (r == n) { count++; return; }
    for (int c = 0; c < n; c++) {
        if (cols.contains(c) || d1.contains(r + c) || d2.contains(r - c)) continue;
        cols.add(c); d1.add(r + c); d2.add(r - c);
        backtrack(n, r + 1, cols, d1, d2);
        cols.remove(c); d1.remove(r + c); d2.remove(r - c);
    }
}
```

**複雜度：** O(n!) 時間，O(n) 空間。
