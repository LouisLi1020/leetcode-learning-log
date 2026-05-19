# LC 73 · Set Matrix Zeroes

| 項目 | 內容 |
|------|------|
| Pattern | In-place markers |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/) |

**題意：** 若元素為 0，其所在整行整列都變 0（原地）。

**核心：** 用 **第一行/列 + 兩旗標** 記錄是否要清零，第二遍依標記更新。

```java
public void setZeroes(int[][] matrix) {
    boolean row0 = false, col0 = false;
    int m = matrix.length, n = matrix[0].length;
    for (int i = 0; i < m; i++)
        for (int j = 0; j < n; j++)
            if (matrix[i][j] == 0) {
                if (i == 0) row0 = true; else matrix[i][0] = 0;
                if (j == 0) col0 = true; else matrix[0][j] = 0;
            }
    for (int i = 1; i < m; i++)
        for (int j = 1; j < n; j++)
            if (matrix[i][0] == 0 || matrix[0][j] == 0) matrix[i][j] = 0;
    if (row0) Arrays.fill(matrix[0], 0);
    if (col0) for (int i = 0; i < m; i++) matrix[i][0] = 0;
}
```

**複雜度：** 時間 O(mn) · 空間 O(1)
