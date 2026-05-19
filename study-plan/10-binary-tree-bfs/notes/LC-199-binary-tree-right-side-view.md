# LC 199 · Binary Tree Right Side View

| 項目 | 內容 |
|------|------|
| Pattern | BFS |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/) |

**題意：** 從右側看二元樹，回傳每層最右節點值（由上到下）。

**核心：** BFS 層序：每層最後一個節點加入答案。

```java
public List<Integer> rightSideView(TreeNode root) {
    List<Integer> ans = new ArrayList<>();
    if (root == null) return ans;
    Queue<TreeNode> q = new ArrayDeque<>();
    q.offer(root);
    while (!q.isEmpty()) {
        int size = q.size();
        for (int i = 0; i < size; i++) {
            TreeNode node = q.poll();
            if (node.left != null) q.offer(node.left);
            if (node.right != null) q.offer(node.right);
            if (i == size - 1) ans.add(node.val);
        }
    }
    return ans;
}
```

**複雜度：** O(n) 時間，O(w) 空間（w=最寬層寬度）。
