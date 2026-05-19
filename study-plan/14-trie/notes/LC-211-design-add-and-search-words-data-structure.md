# LC 211 · Design Add and Search Words Data Structure

| 項目 | 內容 |
|------|------|
| Pattern | Trie + DFS |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Design Add and Search Words Data Structure](https://leetcode.com/problems/design-add-and-search-words-data-structure/) |

**題意：** Trie + 支援 `.` 萬用字元（可配任意字母）的 search。

**核心：** insert 同 Trie；search 遇 `.` DFS 嘗試 26 子節點，其餘照常走。

```java
class WordDictionary {
    class Node {
        Node[] next = new Node[26];
        boolean end;
    }
    Node root = new Node();

    public void addWord(String word) {
        Node cur = root;
        for (char c : word.toCharArray()) {
            int i = c - 'a';
            if (cur.next[i] == null) cur.next[i] = new Node();
            cur = cur.next[i];
        }
        cur.end = true;
    }
    public boolean search(String word) {
        return dfs(root, word, 0);
    }
    boolean dfs(Node node, String word, int idx) {
        if (idx == word.length()) return node.end;
        char c = word.charAt(idx);
        if (c == '.') {
            for (Node child : node.next)
                if (child != null && dfs(child, word, idx + 1)) return true;
            return false;
        }
        int i = c - 'a';
        return node.next[i] != null && dfs(node.next[i], word, idx + 1);
    }
}
```

**複雜度：** add O(L)；search 最壞 O(26^L)。
