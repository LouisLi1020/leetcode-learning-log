# LC 427 · Construct Quad Tree

| 項目 | 內容 |
|------|------|
| Pattern | Divide |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Construct Quad Tree](https://leetcode.com/problems/construct-quad-tree/) |

**題意：** 依 2×2 區塊是否全 0/全 1 遞迴建四叉樹。

**核心：** **分治：** 若區域均質 → 葉節點；否則 `isLeaf=false`，四等分遞迴 `construct`。

```java
public Node construct(int[][] grid) {
    return build(grid, 0, 0, grid.length);
}
Node build(int[][] g, int r, int c, int len) {
    boolean same = true;
    int v = g[r][c];
    for (int i = r; i < r + len && same; i++)
        for (int j = c; j < c + len; j++)
            if (g[i][j] != v) same = false;
    Node node = new Node(same, v == 1);
    if (!same) {
        int h = len / 2;
        node.topLeft = build(g, r, c, h);
        node.topRight = build(g, r, c + h, h);
        node.bottomLeft = build(g, r + h, c, h);
        node.bottomRight = build(g, r + h, c + h, h);
    }
    return node;
}
```

**複雜度：** 時間 O(n²) · 空間 O(log n)
