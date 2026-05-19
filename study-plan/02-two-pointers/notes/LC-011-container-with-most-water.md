# LC 11 · Container With Most Water

| 項目 | 內容 |
|------|------|
| Pattern | Two pointers |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Container With Most Water](https://leetcode.com/problems/container-with-most-water/) |

**題意：** n 條垂線，找兩線與 x 軸圍成最大面積。

**核心：** 雙指標：**矮邊決定寬**，移動矮邊，面積 (r-l)*min(h[l],h[r])。

```java
public int maxArea(int[] height) {
    int l = 0, r = height.length - 1, ans = 0;
    while (l < r) {
        ans = Math.max(ans, Math.min(height[l], height[r]) * (r - l));
        if (height[l] < height[r]) l++; else r--;
    }
    return ans;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
