# LC 300 · Longest Increasing Subsequence

| 項目 | 內容 |
|------|------|
| Pattern | DP + BS |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/) |

**題意：** 最長嚴格遞增子序列長度。

**核心：** **耐心排序：** `tails[len]` 為長度 `len+1` 子序列最小尾；二分插入 `num`。

O(n²) DP：`dp[i]=1+max(dp[j])` 且 `nums[j]<nums[i]`。

```java
public int lengthOfLIS(int[] nums) {
    int[] tails = new int[nums.length];
    int len = 0;
    for (int x : nums) {
        int lo = 0, hi = len;
        while (lo < hi) {
            int mid = lo + (hi - lo) / 2;
            if (tails[mid] < x) lo = mid + 1;
            else hi = mid;
        }
        tails[lo] = x;
        if (lo == len) len++;
    }
    return len;
}
```

**複雜度：** 時間 O(n log n) · 空間 O(n)
