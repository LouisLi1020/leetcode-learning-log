# LC 54 · Spiral Matrix

| 項目 | 內容 |
|------|------|
| Pattern | Simulation |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Spiral Matrix](https://leetcode.com/problems/spiral-matrix/) |

**題意：** 順時針螺旋輸出矩陣所有元素。

**核心：** 四邊界 **top/bottom/left/right**，每圈依序走右→下→左→上。

```java
public List<Integer> spiralOrder(int[][] matrix) {
    List<Integer> res = new ArrayList<>();
    int top = 0, bottom = matrix.length - 1, left = 0, right = matrix[0].length - 1;
    while (top <= bottom && left <= right) {
        for (int c = left; c <= right; c++) res.add(matrix[top][c]);
        top++;
        for (int r = top; r <= bottom; r++) res.add(matrix[r][right]);
        right--;
        if (top <= bottom) {
            for (int c = right; c >= left; c--) res.add(matrix[bottom][c]);
            bottom--;
        }
        if (left <= right) {
            for (int r = bottom; r >= top; r--) res.add(matrix[r][left]);
            left++;
        }
    }
    return res;
}
```

**複雜度：** 時間 O(mn) · 空間 O(1) 不含輸出
