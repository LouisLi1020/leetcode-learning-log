# LC 228 · Summary Ranges

| 項目 | 內容 |
|------|------|
| Pattern | Scan |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Summary Ranges](https://leetcode.com/problems/summary-ranges/) |

**題意：** 已排序無重複陣列合併連續區間為字串列表。

**核心：** 掃描起點 start，直到 nums[i]!=nums[i-1]+1 輸出區間。

```java
public List<String> summaryRanges(int[] nums) {
    List<String> res = new ArrayList<>();
    for (int i = 0; i < nums.length; i++) {
        int start = nums[i];
        while (i + 1 < nums.length && nums[i + 1] == nums[i] + 1) i++;
        if (start == nums[i]) res.add(String.valueOf(start));
        else res.add(start + "->" + nums[i]);
    }
    return res;
}
```

**複雜度：** 時間 O(n) · 空間 O(1) 不含輸出
