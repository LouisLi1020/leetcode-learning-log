# LC 80 · Remove Duplicates from Sorted Array II

| 項目 | 內容 |
|------|------|
| Pattern | Read/write |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Remove Duplicates from Sorted Array II](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/) |

**題意：** 已排序陣列，每個值最多保留 2 個，原地操作。

**核心：** LC26 升級：與 **nums[k-2]** 比較（已排序下每值最多兩次）。

```java
public int removeDuplicates(int[] nums) {
    if (nums.length <= 2) return nums.length;
    int k = 2;
    for (int i = 2; i < nums.length; i++) {
        if (nums[i] != nums[k - 2]) nums[k++] = nums[i];
    }
    return k;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
