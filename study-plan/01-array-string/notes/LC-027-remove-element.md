# LC 27 · Remove Element

| 項目 | 內容 |
|------|------|
| Pattern | Read/write pointers |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Remove Element](https://leetcode.com/problems/remove-element/) |

**題意：** 原地移除所有等於 val 的元素，回傳 k，前 k 格為有效值。

**核心：** **read/write**：i 掃描，k 為下一寫入位置，把「不是 val」往前搬。

| 指標 | 角色 |
|------|------|
| i | 讀 |
| k | 寫 |

```java
public int removeElement(int[] nums, int val) {
    int k = 0;
    for (int i = 0; i < nums.length; i++) {
        if (nums[i] != val) nums[k++] = nums[i];
    }
    return k;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
