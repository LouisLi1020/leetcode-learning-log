# LC 198 · House Robber

| 項目 | 內容 |
|------|------|
| Pattern | DP |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [House Robber](https://leetcode.com/problems/house-robber/) |

**題意：** 不能搶相鄰房屋，求最大贓款。

**核心：** `dp[i]=max(dp[i-1], dp[i-2]+nums[i])`；`prev`/`curr` 滾動。

```java
public int rob(int[] nums) {
    int prev = 0, curr = 0;
    for (int x : nums) {
        int tmp = curr;
        curr = Math.max(curr, prev + x);
        prev = tmp;
    }
    return curr;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
