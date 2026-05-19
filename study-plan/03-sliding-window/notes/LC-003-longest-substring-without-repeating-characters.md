# LC 3 · Longest Substring Without Repeating Characters

| 項目 | 內容 |
|------|------|
| Pattern | Sliding window |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/) |

**題意：** 最長不含重複字元的子字串長度。

**核心：** HashMap 存字元最後索引；**l 跳到重複處+1**。

```java
public int lengthOfLongestSubstring(String s) {
    Map<Character, Integer> last = new HashMap<>();
    int l = 0, ans = 0;
    for (int r = 0; r < s.length(); r++) {
        char c = s.charAt(r);
        if (last.containsKey(c)) l = Math.max(l, last.get(c) + 1);
        last.put(c, r);
        ans = Math.max(ans, r - l + 1);
    }
    return ans;
}
```

**複雜度：** 時間 O(n) · 空間 O(min(n,Σ))
