# LC 26 · Remove Duplicates from Sorted Array

| 項目 | 內容 |
|------|------|
| Pattern | Read/write |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/) |

**題意：** 已排序陣列原地去重，回傳唯一元素個數 k。

**核心：** 已排序→重複連續；**overwrite**：nums[i] 與 nums[k-1] 不同才寫入 k。

```java
public int removeDuplicates(int[] nums) {
    if (nums.length == 0) return 0;
    int k = 1;
    for (int i = 1; i < nums.length; i++) {
        if (nums[i] != nums[k - 1]) nums[k++] = nums[i];
    }
    return k;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
