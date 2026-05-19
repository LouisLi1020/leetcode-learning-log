# LC 169 · Majority Element

| 項目 | 內容 |
|------|------|
| Pattern | Boyer–Moore |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Majority Element](https://leetcode.com/problems/majority-element/) |

**題意：** 找出出現次數 > n/2 的多數元素（保證存在）。

**核心：** **Boyer–Moore 投票**：candidate + count，相同 +1 不同 -1，歸零換人。

```java
public int majorityElement(int[] nums) {
    int candidate = 0, count = 0;
    for (int num : nums) {
        if (count == 0) candidate = num;
        count += (num == candidate) ? 1 : -1;
    }
    return candidate;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
