# LC 71 · Simplify Path

| 項目 | 內容 |
|------|------|
| Pattern | Stack |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Simplify Path](https://leetcode.com/problems/simplify-path/) |

**題意：** Unix 風格路徑簡化（. 與 ..）。

**核心：** split `/`，**Stack** 遇 .. pop、遇 . 忽略、否則 push。

```java
public String simplifyPath(String path) {
    Deque<String> st = new ArrayDeque<>();
    for (String part : path.split("/")) {
        if (part.isEmpty() || part.equals(".")) continue;
        if (part.equals("..")) { if (!st.isEmpty()) st.pop(); }
        else st.push(part);
    }
    StringBuilder sb = new StringBuilder();
    for (String p : st) sb.append('/').append(p);
    return sb.length() == 0 ? "/" : sb.toString();
}
```

**複雜度：** 時間 O(n) · 空間 O(n)
