# LC 55 · Jump Game

| 項目 | 內容 |
|------|------|
| Pattern | Greedy backward |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Jump Game](https://leetcode.com/problems/jump-game/) |

**題意：** nums[i] 表示從 i 最多跳 nums[i] 步，能否到達最後一格。

**核心：** 從尾往前：**goal** 初始 n-1，若 i+nums[i]>=goal 則 goal=i，最後 goal==0。

```java
public boolean canJump(int[] nums) {
    int goal = nums.length - 1;
    for (int i = nums.length - 2; i >= 0; i--) {
        if (i + nums[i] >= goal) goal = i;
    }
    return goal == 0;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
