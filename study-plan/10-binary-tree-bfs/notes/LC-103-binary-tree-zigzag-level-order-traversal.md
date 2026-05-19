# LC 103 · Binary Tree Zigzag Level Order Traversal

| 項目 | 內容 |
|------|------|
| Pattern | BFS |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/) |

**題意：** 鋸齒形（zigzag）層序遍歷：奇數層左→右，偶數層右→左。

**核心：** BFS 同 102，用 `leftToRight` 旗標決定加入 level 頭或尾。

```java
public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
    List<List<Integer>> ans = new ArrayList<>();
    if (root == null) return ans;
    Queue<TreeNode> q = new ArrayDeque<>();
    q.offer(root);
    boolean leftToRight = true;
    while (!q.isEmpty()) {
        int size = q.size();
        LinkedList<Integer> level = new LinkedList<>();
        for (int i = 0; i < size; i++) {
            TreeNode node = q.poll();
            if (leftToRight) level.addLast(node.val);
            else level.addFirst(node.val);
            if (node.left != null) q.offer(node.left);
            if (node.right != null) q.offer(node.right);
        }
        ans.add(level);
        leftToRight = !leftToRight;
    }
    return ans;
}
```

**複雜度：** O(n) 時間，O(w) 空間。
