# LC 48 · Rotate Image

| 項目 | 內容 |
|------|------|
| Pattern | Transpose + reverse |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Rotate Image](https://leetcode.com/problems/rotate-image/) |

**題意：** 原地將 n×n 矩陣順時針轉 90°。

**核心：** 先 **transpose** 再每行 **reverse**。

```java
public void rotate(int[][] matrix) {
    int n = matrix.length;
    for (int i = 0; i < n; i++)
        for (int j = i + 1; j < n; j++) {
            int t = matrix[i][j]; matrix[i][j] = matrix[j][i]; matrix[j][i] = t;
        }
    for (int[] row : matrix) {
        int l = 0, r = row.length - 1;
        while (l < r) { int t = row[l]; row[l++] = row[r]; row[r--] = t; }
    }
}
```

**複雜度：** 時間 O(n²) · 空間 O(1)
