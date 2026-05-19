# LC 129 · Sum Root to Leaf Numbers

| 項目 | 內容 |
|------|------|
| Pattern | DFS |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Sum Root to Leaf Numbers](https://leetcode.com/problems/sum-root-to-leaf-numbers/) |

**題意：** 加總所有根到葉路徑形成的整數（如 1→2→3 代表 123）。

**核心：** DFS：`num = num * 10 + root.val`；葉節點回傳 num，否則加總左右。

```java
public int sumNumbers(TreeNode root) {
    return dfs(root, 0);
}
int dfs(TreeNode node, int num) {
    if (node == null) return 0;
    num = num * 10 + node.val;
    if (node.left == null && node.right == null) return num;
    return dfs(node.left, num) + dfs(node.right, num);
}
```

**複雜度：** O(n) 時間，O(h) 空間。
