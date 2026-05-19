# LC 53 · Maximum Subarray

| 項目 | 內容 |
|------|------|
| Pattern | Kadane |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/) |

**題意：** 求連續子陣列最大和。

**核心：** **Kadane：** `cur = max(nums[i], cur + nums[i])`，`best = max(best, cur)`；負數累積不如重開。

```java
public int maxSubArray(int[] nums) {
    int cur = nums[0], best = nums[0];
    for (int i = 1; i < nums.length; i++) {
        cur = Math.max(nums[i], cur + nums[i]);
        best = Math.max(best, cur);
    }
    return best;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
