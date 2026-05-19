# LC 6 · Zigzag Conversion

| 項目 | 內容 |
|------|------|
| Pattern | Simulation |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Zigzag Conversion](https://leetcode.com/problems/zigzag-conversion/) |

**題意：** 按 Z 字形排列字串，numRows 行。

**核心：** 模擬 **row + direction**：到頂/底反轉方向，最後拼接各行。

```java
public String convert(String s, int numRows) {
    if (numRows == 1) return s;
    StringBuilder[] rows = new StringBuilder[numRows];
    for (int i = 0; i < numRows; i++) rows[i] = new StringBuilder();
    int row = 0, dir = -1;
    for (char c : s.toCharArray()) {
        rows[row].append(c);
        if (row == 0 || row == numRows - 1) dir *= -1;
        row += dir;
    }
    StringBuilder ans = new StringBuilder();
    for (StringBuilder r : rows) ans.append(r);
    return ans.toString();
}
```

**複雜度：** 時間 O(n) · 空間 O(n)
