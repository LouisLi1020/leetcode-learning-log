# LC 17 · Letter Combinations of a Phone Number

| 項目 | 內容 |
|------|------|
| Pattern | Backtrack |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/) |

**題意：** 電話數字鍵 2–9，回傳所有可能的字母組合。

**核心：** 回溯：digits 逐位展開對應字母表，path 到長度即加入 ans。

```java
String[] map = {"","", "abc","def","ghi","jkl","mno","pqrs","tuv","wxyz"};

public List<String> letterCombinations(String digits) {
    List<String> ans = new ArrayList<>();
    if (digits.isEmpty()) return ans;
    backtrack(digits, 0, new StringBuilder(), ans);
    return ans;
}
void backtrack(String digits, int i, StringBuilder path, List<String> ans) {
    if (i == digits.length()) { ans.add(path.toString()); return; }
    for (char c : map[digits.charAt(i) - '0'].toCharArray()) {
        path.append(c);
        backtrack(digits, i + 1, path, ans);
        path.deleteCharAt(path.length() - 1);
    }
}
```

**複雜度：** O(4^n·n) 時間，O(n) 空間（不含輸出）。
