# LC 34 · Find First and Last Position of Element in Sorted Array

| 項目 | 內容 |
|------|------|
| Pattern | Binary search |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/) |

**題意：** 升序陣列中 `target` 的起始與結束位置。

**核心：** 兩次二分：左界（第一個 ≥ target）、右界（第一個 > target）−1。

```java
public int[] searchRange(int[] nums, int target) {
    int left = lowerBound(nums, target);
    if (left == nums.length || nums[left] != target) return new int[]{-1, -1};
    int right = lowerBound(nums, target + 1) - 1;
    return new int[]{left, right};
}
int lowerBound(int[] nums, int t) {
    int lo = 0, hi = nums.length;
    while (lo < hi) {
        int mid = lo + (hi - lo) / 2;
        if (nums[mid] < t) lo = mid + 1;
        else hi = mid;
    }
    return lo;
}
```

**複雜度：** 時間 O(log n) · 空間 O(1)
