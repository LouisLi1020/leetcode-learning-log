# LC 106 · Construct Binary Tree from Inorder and Postorder Traversal

| 項目 | 內容 |
|------|------|
| Pattern | Divide |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Construct Binary Tree from Inorder and Postorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/) |

**題意：** 給 inorder + postorder，重建唯一二元樹。

**核心：** postorder 最後一個是根；inorder 找根切左右；先建右再建左（post 從尾往前讀）。

```java
int postIdx;
Map<Integer, Integer> idx = new HashMap<>();

public TreeNode buildTree(int[] inorder, int[] postorder) {
    for (int i = 0; i < inorder.length; i++) idx.put(inorder[i], i);
    postIdx = postorder.length - 1;
    return build(inorder, 0, inorder.length - 1, postorder);
}
TreeNode build(int[] in, int inL, int inR, int[] post) {
    if (inL > inR) return null;
    int rootVal = post[postIdx--];
    TreeNode root = new TreeNode(rootVal);
    int mid = idx.get(rootVal);
    root.right = build(in, mid + 1, inR, post);
    root.left = build(in, inL, mid - 1, post);
    return root;
}
```

**複雜度：** O(n) 時間，O(n) 空間。
