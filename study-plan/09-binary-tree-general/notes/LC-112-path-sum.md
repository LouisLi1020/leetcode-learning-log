# LC 112 · Path Sum

| 項目 | 內容 |
|------|------|
| Pattern | DFS |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Path Sum](https://leetcode.com/problems/path-sum/) |

**題意：** 是否存在根到葉路徑，節點值總和等於 targetSum。

**核心：** DFS 帶累加和：到葉時若 sum==target 回 true；左右 OR。

```java
public boolean hasPathSum(TreeNode root, int targetSum) {
    if (root == null) return false;
    if (root.left == null && root.right == null)
        return root.val == targetSum;
    return hasPathSum(root.left, targetSum - root.val)
        || hasPathSum(root.right, targetSum - root.val);
}
```

**複雜度：** O(n) 時間，O(h) 空間。
