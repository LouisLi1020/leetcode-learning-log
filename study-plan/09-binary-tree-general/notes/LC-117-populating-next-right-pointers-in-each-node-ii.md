# LC 117 · Populating Next Right Pointers in Each Node II

| 項目 | 內容 |
|------|------|
| Pattern | BFS |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Populating Next Right Pointers in Each Node II](https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/) |

**題意：** 完美二元樹以外，將每層節點 next 指標指向同層右側鄰居。

**核心：** BFS 層序：用 dummy 節點串起下一層鏈，逐層建立 next 指標。

```java
public Node connect(Node root) {
    if (root == null) return null;
    Node level = root;
    while (level != null) {
        Node dummy = new Node(0);
        Node tail = dummy;
        for (Node cur = level; cur != null; cur = cur.next) {
            if (cur.left != null) { tail.next = cur.left; tail = tail.next; }
            if (cur.right != null) { tail.next = cur.right; tail = tail.next; }
        }
        level = dummy.next;
    }
    return root;
}
```

**複雜度：** O(n) 時間，O(1) 額外空間。
