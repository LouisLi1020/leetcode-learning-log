# LC 127 · Word Ladder

| 項目 | 內容 |
|------|------|
| Pattern | BFS |
| 難度 | Hard |
| 狀態 | **done** |
| 題目 | [Word Ladder](https://leetcode.com/problems/word-ladder/) |

**題意：** 單字接龍：beginWord 到 endWord 最短轉換序列長度（每次改一字母且在中間 wordList）。

**核心：** BFS 逐層：對當前 word 的每個位置試 26 字母；在 wordSet 則入隊。雙向 BFS 可加速。

雙向 BFS 從首尾同時擴展，相遇層數相加。

```java
public int ladderLength(String beginWord, String endWord, List<String> wordList) {
    Set<String> dict = new HashSet<>(wordList);
    if (!dict.contains(endWord)) return 0;
    Queue<String> q = new ArrayDeque<>();
    q.offer(beginWord);
    int level = 1;
    while (!q.isEmpty()) {
        int size = q.size();
        for (int i = 0; i < size; i++) {
            char[] word = q.poll().toCharArray();
            for (int j = 0; j < word.length; j++) {
                char orig = word[j];
                for (char c = 'a'; c <= 'z'; c++) {
                    word[j] = c;
                    String next = new String(word);
                    if (next.equals(endWord)) return level + 1;
                    if (dict.remove(next)) q.offer(next);
                }
                word[j] = orig;
            }
        }
        level++;
    }
    return 0;
}
```

**複雜度：** O(N·L²·26) 時間，O(N) 空間。
