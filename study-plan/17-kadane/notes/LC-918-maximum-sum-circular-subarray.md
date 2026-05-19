# LC 918 · Maximum Sum Circular Subarray

| 項目 | 內容 |
|------|------|
| Pattern | Kadane variant |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Maximum Sum Circular Subarray](https://leetcode.com/problems/maximum-sum-circular-subarray/) |

**題意：** 環形陣列的最大子陣列和。

**核心：** 一般 Kadane 最大和 **或** `total - minSubarray`（跨首尾）；若全負數則答案為 Kadane 最大（不用環形）。

| 情況 | 公式 |
|------|------|
| 一般 | max(Kadane max, sum - Kadane min) |
| 全負 | Kadane max |

```java
public int maxSubarraySumCircular(int[] nums) {
    int total = 0, maxSum = nums[0], minSum = nums[0];
    int curMax = nums[0], curMin = nums[0];
    for (int i = 1; i < nums.length; i++) {
        total += nums[i];
        curMax = Math.max(nums[i], curMax + nums[i]);
        maxSum = Math.max(maxSum, curMax);
        curMin = Math.min(nums[i], curMin + nums[i]);
        minSum = Math.min(minSum, curMin);
    }
    return maxSum > 0 ? Math.max(maxSum, total - minSum) : maxSum;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
