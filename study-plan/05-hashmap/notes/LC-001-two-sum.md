# LC 1 · Two Sum

| 項目 | 內容 |
|------|------|
| Pattern | Hash map |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Two Sum](https://leetcode.com/problems/two-sum/) |

**題意：** 找兩數和為 target 的索引（恰好一解）。

**核心：** **HashMap** 存 value→index，掃描時查 target-num。

```java
public int[] twoSum(int[] nums, int target) {
    Map<Integer, Integer> map = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
        int need = target - nums[i];
        if (map.containsKey(need)) return new int[]{map.get(need), i};
        map.put(nums[i], i);
    }
    return new int[]{};
}
```

**複雜度：** 時間 O(n) · 空間 O(n)
