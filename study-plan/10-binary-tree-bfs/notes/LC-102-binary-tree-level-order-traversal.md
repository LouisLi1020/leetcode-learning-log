# LC 102 · Binary Tree Level Order Traversal

| 項目 | 內容 |
|------|------|
| Pattern | BFS |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/) |

**題意：** 層序遍歷二元樹，回傳每層節點值列表。

**核心：** BFS：每輪固定 size，依序 poll 同層節點並 push 子節點。

```java
public List<List<Integer>> levelOrder(TreeNode root) {
    List<List<Integer>> ans = new ArrayList<>();
    if (root == null) return ans;
    Queue<TreeNode> q = new ArrayDeque<>();
    q.offer(root);
    while (!q.isEmpty()) {
        int size = q.size();
        List<Integer> level = new ArrayList<>();
        for (int i = 0; i < size; i++) {
            TreeNode node = q.poll();
            level.add(node.val);
            if (node.left != null) q.offer(node.left);
            if (node.right != null) q.offer(node.right);
        }
        ans.add(level);
    }
    return ans;
}
```

**複雜度：** O(n) 時間，O(w) 空間。
