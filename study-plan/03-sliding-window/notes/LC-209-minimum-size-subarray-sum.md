# LC 209 · Minimum Size Subarray Sum

| 項目 | 內容 |
|------|------|
| Pattern | Sliding window |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/) |

**題意：** 長度 ≥ k 且和 ≥ target 的最短子陣列長度，無解回 0。

**核心：** **滑動視窗**：右擴累加 sum，sum≥target 時左縮更新 minLen。

```java
public int minSubArrayLen(int target, int[] nums) {
    int l = 0, sum = 0, minLen = Integer.MAX_VALUE;
    for (int r = 0; r < nums.length; r++) {
        sum += nums[r];
        while (sum >= target) {
            minLen = Math.min(minLen, r - l + 1);
            sum -= nums[l++];
        }
    }
    return minLen == Integer.MAX_VALUE ? 0 : minLen;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
