# LC 208 · Implement Trie (Prefix Tree)

| 項目 | 內容 |
|------|------|
| Pattern | Trie |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/) |

**題意：** 實作 Trie：insert、search（完整字）、startsWith（前綴）。

**核心：** 26 叉樹節點 + isEnd 旗標；insert/search 沿字元走，search 需 isEnd。

```java
class Trie {
    class Node {
        Node[] next = new Node[26];
        boolean end;
    }
    Node root = new Node();

    public void insert(String word) {
        Node cur = root;
        for (char c : word.toCharArray()) {
            int i = c - 'a';
            if (cur.next[i] == null) cur.next[i] = new Node();
            cur = cur.next[i];
        }
        cur.end = true;
    }
    public boolean search(String word) {
        Node node = walk(word);
        return node != null && node.end;
    }
    public boolean startsWith(String prefix) {
        return walk(prefix) != null;
    }
    Node walk(String s) {
        Node cur = root;
        for (char c : s.toCharArray()) {
            int i = c - 'a';
            if (cur.next[i] == null) return null;
            cur = cur.next[i];
        }
        return cur;
    }
}
```

**複雜度：** insert/search/startsWith 皆 O(L) 時間，O(N·L) 空間。
