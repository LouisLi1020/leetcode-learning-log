# LC 124 · Binary Tree Maximum Path Sum

| 項目 | 內容 |
|------|------|
| Pattern | DFS post-order |
| 難度 | Hard |
| 狀態 | **done** |
| 題目 | [Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/) |

**題意：** 求任意節點間路徑的最大和（路徑不必過根；節點值可為負）。

**核心：** 後序 DFS：回傳「以 node 為端點向下延伸的最大單邊和」；跨左右子樹路徑 `leftGain+rightGain+val` 更新 global max。負貢獻截斷為 0。

| 回傳 | 意義 |
|------|------|
| max(leftGain, rightGain) + val | 單邊最大（可接父） |
| globalMax | 含左右跨過 node 的路徑 |

```java
int maxSum = Integer.MIN_VALUE;

public int maxPathSum(TreeNode root) {
    gain(root);
    return maxSum;
}
int gain(TreeNode node) {
    if (node == null) return 0;
    int left = Math.max(gain(node.left), 0);
    int right = Math.max(gain(node.right), 0);
    maxSum = Math.max(maxSum, left + right + node.val);
    return Math.max(left, right) + node.val;
}
```

**複雜度：** O(n) 時間，O(h) 空間。
