# LC 22 · Generate Parentheses

| 項目 | 內容 |
|------|------|
| Pattern | Backtrack |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Generate Parentheses](https://leetcode.com/problems/generate-parentheses/) |

**題意：** n 對括號的所有有效組合（合法匹配）。

**核心：** 回溯：可放 `(` 若 open<n；可放 `)` 若 close<open。

```java
public List<String> generateParenthesis(int n) {
    List<String> ans = new ArrayList<>();
    backtrack(n, 0, 0, new StringBuilder(), ans);
    return ans;
}
void backtrack(int n, int open, int close, StringBuilder path, List<String> ans) {
    if (path.length() == 2 * n) { ans.add(path.toString()); return; }
    if (open < n) {
        path.append('(');
        backtrack(n, open + 1, close, path, ans);
        path.deleteCharAt(path.length() - 1);
    }
    if (close < open) {
        path.append(')');
        backtrack(n, open, close + 1, path, ans);
        path.deleteCharAt(path.length() - 1);
    }
}
```

**複雜度：** O(Catalan(n)·n) 時間，O(n) 空間。
