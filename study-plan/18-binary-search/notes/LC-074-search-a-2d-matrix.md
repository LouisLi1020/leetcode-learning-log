# LC 74 · Search a 2D Matrix

| 項目 | 內容 |
|------|------|
| Pattern | Binary search |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/) |

**題意：** 在列遞增、行內遞增的矩陣中找 `target`。

**核心：** 當成一維升序：`idx = row*n+col`，二分 `0..m*n-1`。

```java
public boolean searchMatrix(int[][] matrix, int target) {
    int m = matrix.length, n = matrix[0].length;
    int lo = 0, hi = m * n - 1;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        int val = matrix[mid / n][mid % n];
        if (val == target) return true;
        if (val < target) lo = mid + 1;
        else hi = mid - 1;
    }
    return false;
}
```

**複雜度：** 時間 O(log(mn)) · 空間 O(1)
