# LC 238 · Product of Array Except Self

| 項目 | 內容 |
|------|------|
| Pattern | Prefix/suffix product |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/) |

**題意：** 回傳陣列 `answer`，其中 `answer[i]` 為除 `nums[i]` 外其餘元素乘積；**不可用除法**。

**核心：** 左掃建 **prefix** 到 `answer`；右掃乘 **suffix**。輸出陣列不計入額外空間。

| 變數 | 意義 |
|------|------|
| `ans[i]` | 左側乘積（第一趟）× 右側乘積（第二趟） |
| `suffix` | 從右往左累積的乘積 |

```java
public int[] productExceptSelf(int[] nums) {
    int n = nums.length;
    int[] ans = new int[n];
    ans[0] = 1;
    for (int i = 1; i < n; i++)
        ans[i] = ans[i - 1] * nums[i - 1];
    int suffix = 1;
    for (int i = n - 1; i >= 0; i--) {
        ans[i] *= suffix;
        suffix *= nums[i];
    }
    return ans;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)（輸出不計）
