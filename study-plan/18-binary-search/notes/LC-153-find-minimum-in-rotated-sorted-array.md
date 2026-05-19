# LC 153 · Find Minimum in Rotated Sorted Array

| 項目 | 內容 |
|------|------|
| Pattern | Binary search |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/) |

**題意：** 旋轉陣列（無重複）的最小元素。

**核心：** 若 `nums[mid] > nums[hi]`，最小在右；否則在左含 `mid`。

```java
public int findMin(int[] nums) {
    int lo = 0, hi = nums.length - 1;
    while (lo < hi) {
        int mid = lo + (hi - lo) / 2;
        if (nums[mid] > nums[hi]) lo = mid + 1;
        else hi = mid;
    }
    return nums[lo];
}
```

**複雜度：** 時間 O(log n) · 空間 O(1)
