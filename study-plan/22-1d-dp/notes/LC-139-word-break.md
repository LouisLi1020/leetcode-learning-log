# LC 139 · Word Break

| 項目 | 內容 |
|------|------|
| Pattern | DP |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Word Break](https://leetcode.com/problems/word-break/) |

**題意：** 字串能否切成字典中的單字。

**核心：** `dp[i]` 表示前 `i` 字元可否拆分；枚舉最後一段 `wordDict` 是否在 `i-len..i`。

```java
public boolean wordBreak(String s, List<String> wordDict) {
    Set<String> set = new HashSet<>(wordDict);
    boolean[] dp = new boolean[s.length() + 1];
    dp[0] = true;
    for (int i = 1; i <= s.length(); i++) {
        for (int j = 0; j < i; j++) {
            if (dp[j] && set.contains(s.substring(j, i))) {
                dp[i] = true;
                break;
            }
        }
    }
    return dp[s.length()];
}
```

**複雜度：** 時間 O(n²·L) · 空間 O(n)
