# LC 49 · Group Anagrams

| 項目 | 內容 |
|------|------|
| Pattern | Hash key |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Group Anagrams](https://leetcode.com/problems/group-anagrams/) |

**題意：** 將字母異位詞分組。

**核心：** 排序字串或 **26 長度計數** 作為 HashMap key。

```java
public List<List<String>> groupAnagrams(String[] strs) {
    Map<String, List<String>> map = new HashMap<>();
    for (String s : strs) {
        char[] a = s.toCharArray();
        Arrays.sort(a);
        String key = new String(a);
        map.computeIfAbsent(key, k -> new ArrayList<>()).add(s);
    }
    return new ArrayList<>(map.values());
}
```

**複雜度：** 時間 O(n·k log k) · 空間 O(nk)
