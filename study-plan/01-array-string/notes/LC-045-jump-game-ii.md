# LC 45 · Jump Game II

| 項目 | 內容 |
|------|------|
| Pattern | BFS window |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Jump Game II](https://leetcode.com/problems/jump-game-ii/) |

**題意：** 保證可達終點，求最少跳躍次數。

**核心：** BFS 層級：**near/far** 視窗，每輪擴展 farthest，跳完 jumps++。

```java
public int jump(int[] nums) {
    int near = 0, far = 0, jumps = 0;
    while (far < nums.length - 1) {
        int farthest = far;
        for (int i = near; i <= far; i++)
            farthest = Math.max(farthest, i + nums[i]);
        near = far + 1;
        far = farthest;
        jumps++;
    }
    return jumps;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
