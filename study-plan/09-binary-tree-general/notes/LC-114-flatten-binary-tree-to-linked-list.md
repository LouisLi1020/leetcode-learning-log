# LC 114 · Flatten Binary Tree to Linked List

| 項目 | 內容 |
|------|------|
| Pattern | DFS |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Flatten Binary Tree to Linked List](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/) |

**題意：** 原地將二元樹按 preorder 順序展平成右指標鏈表（left=null）。

**核心：** 反向前序 DFS：先處理右再左；用 prev 指標把上一節點 right 接到當前節點。

Morris 遍歷可 O(1) 空間，面試常考反向前序 + prev 寫法。

```java
TreeNode prev = null;

public void flatten(TreeNode root) {
    if (root == null) return;
    flatten(root.right);
    flatten(root.left);
    root.right = prev;
    root.left = null;
    prev = root;
}
```

**複雜度：** O(n) 時間，O(h) 空間。
