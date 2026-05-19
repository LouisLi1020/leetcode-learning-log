# LC 219 · Contains Duplicate II

| 項目 | 內容 |
|------|------|
| Pattern | Sliding window + set |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Contains Duplicate II](https://leetcode.com/problems/contains-duplicate-ii/) |

**題意：** 是否存在索引 i,j 使 nums[i]==nums[j] 且 |i-j|≤k。

**核心：** HashMap 存值→最近索引，若同值且距離≤k 則 true。

```java
public boolean containsNearbyDuplicate(int[] nums, int k) {
    Map<Integer, Integer> idx = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
        if (idx.containsKey(nums[i]) && i - idx.get(nums[i]) <= k) return true;
        idx.put(nums[i], i);
    }
    return false;
}
```

**複雜度：** 時間 O(n) · 空間 O(n)
