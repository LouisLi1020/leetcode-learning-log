# LC 149 · Max Points on a Line

| 項目 | 內容 |
|------|------|
| Pattern | Geometry + hash |
| 難度 | Hard |
| 狀態 | **done** |
| 題目 | [Max Points on a Line](https://leetcode.com/problems/max-points-on-a-line/) |

**題意：** 平面上最多幾點共線。

**核心：** 固定一點，用 **HashMap<斜率, 次數>** 統計；注意重複點與 `dx=0` 用特殊鍵。

```java
public int maxPoints(int[][] points) {
    int n = points.length;
    if (n <= 2) return n;
    int ans = 0;
    for (int i = 0; i < n; i++) {
        Map<String, Integer> cnt = new HashMap<>();
        int same = 1, localMax = 0;
        for (int j = i + 1; j < n; j++) {
            int dx = points[j][0] - points[i][0];
            int dy = points[j][1] - points[i][1];
            if (dx == 0 && dy == 0) { same++; continue; }
            int g = gcd(dx, dy);
            dx /= g; dy /= g;
            if (dx < 0) { dx = -dx; dy = -dy; }
            String key = dx + "/" + dy;
            cnt.put(key, cnt.getOrDefault(key, 1) + 1);
            localMax = Math.max(localMax, cnt.get(key));
        }
        ans = Math.max(ans, localMax + same);
    }
    return ans;
}
int gcd(int a, int b) { return b == 0 ? a : gcd(b, a % b); }
```

**複雜度：** 時間 O(n²) · 空間 O(n)
