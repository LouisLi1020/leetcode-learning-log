# LC 212 · Word Search II

| 項目 | 內容 |
|------|------|
| Pattern | Trie + backtrack |
| 難度 | Hard |
| 狀態 | **done** |
| 題目 | [Word Search II](https://leetcode.com/problems/word-search-ii/) |

**題意：** 在 board 上找所有字典詞（可四方向走，同格不重複）。

**核心：** Trie 存 words；DFS backtrack 走 board，沿途縮 Trie；到 isEnd 收集並標記防重。可刪葉優化。

```java
class Node {
    Node[] next = new Node[26];
    String word;
}
Node root = new Node();

public List<String> findWords(char[][] board, String[] words) {
    for (String w : words) insert(w);
    List<String> ans = new ArrayList<>();
    for (int i = 0; i < board.length; i++)
        for (int j = 0; j < board[0].length; j++)
            dfs(board, i, j, root, ans);
    return ans;
}
void insert(String w) {
    Node cur = root;
    for (char c : w.toCharArray()) {
        int i = c - 'a';
        if (cur.next[i] == null) cur.next[i] = new Node();
        cur = cur.next[i];
    }
    cur.word = w;
}
void dfs(char[][] b, int r, int c, Node node, List<String> ans) {
    if (r < 0 || c < 0 || r >= b.length || c >= b[0].length) return;
    char ch = b[r][c];
    if (ch == '#' || node.next[ch - 'a'] == null) return;
    node = node.next[ch - 'a'];
    if (node.word != null) { ans.add(node.word); node.word = null; }
    b[r][c] = '#';
    dfs(b, r + 1, c, node, ans); dfs(b, r - 1, c, node, ans);
    dfs(b, r, c + 1, node, ans); dfs(b, r, c - 1, node, ans);
    b[r][c] = ch;
}
```

**複雜度：** O(mn·4^L) 最壞；Trie 剪枝後實務近 O(mn)。
