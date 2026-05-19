# LC 133 · Clone Graph

| 項目 | 內容 |
|------|------|
| Pattern | BFS/DFS + map |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Clone Graph](https://leetcode.com/problems/clone-graph/) |

**題意：** 深拷貝無向圖（Node 含 val 與 neighbors 列表）。

**核心：** HashMap<原節點, 副本>；DFS/BFS 遇見新節點建副本，遞迴/迭代拷 neighbors。

```java
Map<Node, Node> map = new HashMap<>();

public Node cloneGraph(Node node) {
    if (node == null) return null;
    if (map.containsKey(node)) return map.get(node);
    Node copy = new Node(node.val);
    map.put(node, copy);
    for (Node nei : node.neighbors)
        copy.neighbors.add(cloneGraph(nei));
    return copy;
}
```

**複雜度：** O(V+E) 時間，O(V) 空間。
