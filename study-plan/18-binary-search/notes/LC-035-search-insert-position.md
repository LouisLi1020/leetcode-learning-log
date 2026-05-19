# LC 35 · Search Insert Position

| 項目 | 內容 |
|------|------|
| Pattern | Binary search |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Search Insert Position](https://leetcode.com/problems/search-insert-position/) |

**題意：** 在升序陣列找 `target` 插入位置（第一個 ≥ target）。

**核心：** 標準二分：`lo, hi`，`mid` 左移或右移；結束 `lo` 即插入點。

```java
public int searchInsert(int[] nums, int target) {
    int lo = 0, hi = nums.length;
    while (lo < hi) {
        int mid = lo + (hi - lo) / 2;
        if (nums[mid] < target) lo = mid + 1;
        else hi = mid;
    }
    return lo;
}
```

**複雜度：** 時間 O(log n) · 空間 O(1)
