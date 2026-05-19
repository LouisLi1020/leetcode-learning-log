# LC 42 · Trapping Rain Water

| 項目 | 內容 |
|------|------|
| Pattern | Two pointers / stack |
| 難度 | Hard |
| 狀態 | **done** |
| 題目 | [Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/) |

**題意：** 非負高度柱狀圖，求能接的雨水總量。

**核心：** **雙指標** l/r 維護 lMax/rMax，矮邊決定蓄水並移動。

```java
public int trap(int[] height) {
    int l = 0, r = height.length - 1, lMax = 0, rMax = 0, ans = 0;
    while (l < r) {
        if (height[l] < height[r]) {
            if (height[l] >= lMax) lMax = height[l];
            else ans += lMax - height[l];
            l++;
        } else {
            if (height[r] >= rMax) rMax = height[r];
            else ans += rMax - height[r];
            r--;
        }
    }
    return ans;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
