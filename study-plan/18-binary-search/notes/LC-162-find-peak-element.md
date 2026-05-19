# LC 162 · Find Peak Element

| 項目 | 內容 |
|------|------|
| Pattern | Binary search |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Find Peak Element](https://leetcode.com/problems/find-peak-element/) |

**題意：** 找任一峰值（比左右鄰居大）。

**核心：** 若 `mid < mid+1`，峰值在右；否則在左（含 `mid`）。

```java
public int findPeakElement(int[] nums) {
    int lo = 0, hi = nums.length - 1;
    while (lo < hi) {
        int mid = lo + (hi - lo) / 2;
        if (nums[mid] < nums[mid + 1]) lo = mid + 1;
        else hi = mid;
    }
    return lo;
}
```

**複雜度：** 時間 O(log n) · 空間 O(1)
