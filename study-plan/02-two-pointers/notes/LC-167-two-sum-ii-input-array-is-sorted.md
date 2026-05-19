# LC 167 · Two Sum II - Input Array Is Sorted

| 項目 | 內容 |
|------|------|
| Pattern | Two pointers |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/) |

**題意：** 已排序陣列找兩數和為 target，回傳 1-based 索引。

**核心：** 左右指標：**和太小 l++，太大 r--**。

```java
public int[] twoSum(int[] numbers, int target) {
    int l = 0, r = numbers.length - 1;
    while (l < r) {
        int sum = numbers[l] + numbers[r];
        if (sum == target) return new int[]{l + 1, r + 1};
        if (sum < target) l++; else r--;
    }
    return new int[]{-1, -1};
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
