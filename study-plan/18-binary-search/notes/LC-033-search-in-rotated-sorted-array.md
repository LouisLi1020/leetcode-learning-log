# LC 33 · Search in Rotated Sorted Array

| 項目 | 內容 |
|------|------|
| Pattern | Binary search |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/) |

**題意：** 在旋轉升序陣列中搜尋 `target`。

**核心：** 判斷 `mid` 在左段或右段有序，再決定往左/右；或先找最小值再二分。

```java
public int search(int[] nums, int target) {
    int lo = 0, hi = nums.length - 1;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        if (nums[mid] == target) return mid;
        if (nums[lo] <= nums[mid]) {
            if (nums[lo] <= target && target < nums[mid]) hi = mid - 1;
            else lo = mid + 1;
        } else {
            if (nums[mid] < target && target <= nums[hi]) lo = mid + 1;
            else hi = mid - 1;
        }
    }
    return -1;
}
```

**複雜度：** 時間 O(log n) · 空間 O(1)
