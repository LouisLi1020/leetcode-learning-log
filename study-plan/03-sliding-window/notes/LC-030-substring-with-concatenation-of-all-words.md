# LC 30 · Substring with Concatenation of All Words

| 項目 | 內容 |
|------|------|
| Pattern | Sliding window |
| 難度 | Hard |
| 狀態 | **done** |
| 題目 | [Substring with Concatenation of All Words](https://leetcode.com/problems/substring-with-concatenation-of-all-words/) |

**題意：** s 中找所有包含 words 全部單字串接（順序任意、相鄰）的起始索引。

**核心：** 固定視窗長度 wordLen*wordCount；**雙 HashMap** 比對視窗內字頻。

```java
public List<Integer> findSubstring(String s, String[] words) {
    List<Integer> res = new ArrayList<>();
    if (words.length == 0) return res;
    int wLen = words[0].length(), count = words.length;
    Map<String, Integer> need = new HashMap<>();
    for (String w : words) need.put(w, need.getOrDefault(w, 0) + 1);
    for (int i = 0; i < wLen; i++) {
        int l = i, matched = 0;
        Map<String, Integer> win = new HashMap<>();
        for (int r = i; r + wLen <= s.length(); r += wLen) {
            String sub = s.substring(r, r + wLen);
            if (!need.containsKey(sub)) { l = r + wLen; win.clear(); matched = 0; continue; }
            win.put(sub, win.getOrDefault(sub, 0) + 1);
            matched++;
            while (win.get(sub) > need.get(sub)) {
                String left = s.substring(l, l + wLen);
                if (win.get(left) == 1) win.remove(left); else win.put(left, win.get(left) - 1);
                matched--; l += wLen;
            }
            if (matched == count) res.add(l);
        }
    }
    return res;
}
```

**複雜度：** 時間 O(n·wordLen) · 空間 O(m)
