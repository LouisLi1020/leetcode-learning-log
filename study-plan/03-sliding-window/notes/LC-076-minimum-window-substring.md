# LC 76 · Minimum Window Substring

| 項目 | 內容 |
|------|------|
| Pattern | Sliding window |
| 難度 | Hard |
| 狀態 | **done** |
| 題目 | [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/) |

**題意：** 含 t 所有字元（含重複）的最短 s 子字串。

**核心：** 滑動視窗 + **need/have** 計數，have==needSize 時收縮左界。

```java
public String minWindow(String s, String t) {
    if (t.isEmpty()) return "";
    Map<Character, Integer> need = new HashMap<>();
    for (char c : t.toCharArray()) need.put(c, need.getOrDefault(c, 0) + 1);
    int needSize = need.size(), have = 0, l = 0;
    Map<Character, Integer> win = new HashMap<>();
  int[] res = {-1, 0, 0};
    for (int r = 0; r < s.length(); r++) {
        char c = s.charAt(r);
        win.put(c, win.getOrDefault(c, 0) + 1);
        if (need.containsKey(c) && win.get(c).intValue() == need.get(c).intValue()) have++;
        while (have == needSize) {
            if (res[0] == -1 || r - l + 1 < res[0]) { res[0] = r - l + 1; res[1] = l; res[2] = r; }
            char left = s.charAt(l++);
            win.put(left, win.get(left) - 1);
            if (need.containsKey(left) && win.get(left) < need.get(left)) have--;
        }
    }
    return res[0] == -1 ? "" : s.substring(res[1], res[2] + 1);
}
```

**複雜度：** 時間 O(|s|+|t|) · 空間 O(Σ)
