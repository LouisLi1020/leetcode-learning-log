# LC 36 · Valid Sudoku

| 項目 | 內容 |
|------|------|
| Pattern | Hash sets |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Valid Sudoku](https://leetcode.com/problems/valid-sudoku/) |

**題意：** 9×9 數獨是否有效（行列宮無重複 1–9）。

**核心：** 三個 **HashSet**（或位元）記錄行、列、宮已見數字。

```java
public boolean isValidSudoku(char[][] board) {
    Set<String> seen = new HashSet<>();
    for (int r = 0; r < 9; r++) {
        for (int c = 0; c < 9; c++) {
            char v = board[r][c];
            if (v == '.') continue;
            String key = v + "@" + r + "," + c + "," + (r/3) + (c/3);
            if (!seen.add(v + "r" + r) || !seen.add(v + "c" + c) || !seen.add(v + "b" + r/3 + c/3))
                return false;
        }
    }
    return true;
}
```

**複雜度：** 時間 O(81) · 空間 O(81)
