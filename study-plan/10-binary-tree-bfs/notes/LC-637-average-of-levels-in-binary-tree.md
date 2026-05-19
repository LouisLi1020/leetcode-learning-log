# LC 637 · Average of Levels in Binary Tree

| 項目 | 內容 |
|------|------|
| Pattern | BFS |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Average of Levels in Binary Tree](https://leetcode.com/problems/average-of-levels-in-binary-tree/) |

**題意：** 回傳每層節點值的平均數。

**核心：** BFS 層序：每層累加 sum 與 count，推入 sum/count。

```java
public List<Double> averageOfLevels(TreeNode root) {
    List<Double> ans = new ArrayList<>();
    if (root == null) return ans;
    Queue<TreeNode> q = new ArrayDeque<>();
    q.offer(root);
    while (!q.isEmpty()) {
        int size = q.size();
        double sum = 0;
        for (int i = 0; i < size; i++) {
            TreeNode node = q.poll();
            sum += node.val;
            if (node.left != null) q.offer(node.left);
            if (node.right != null) q.offer(node.right);
        }
        ans.add(sum / size);
    }
    return ans;
}
```

**複雜度：** O(n) 時間，O(w) 空間。
