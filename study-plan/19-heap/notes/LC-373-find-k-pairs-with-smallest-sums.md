# LC 373 · Find K Pairs with Smallest Sums

| 項目 | 內容 |
|------|------|
| Pattern | Heap |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Find K Pairs with Smallest Sums](https://leetcode.com/problems/find-k-pairs-with-smallest-sums/) |

**題意：** 兩升序陣列和最小的 k 個數對 `(i,j)`。

**核心：** 先推 `(0,j)` 共 `min(k,n)` 個；**最小堆** 彈出後若 `i+1<m` 再推 `(i+1,j)`。

```java
public List<List<Integer>> kSmallestPairs(int[] nums1, int[] nums2, int k) {
    List<List<Integer>> res = new ArrayList<>();
    if (nums1.length == 0 || nums2.length == 0 || k == 0) return res;
    PriorityQueue<int[]> pq = new PriorityQueue<>((a, b) ->
        (nums1[a[0]] + nums2[a[1]]) - (nums1[b[0]] + nums2[b[1]]));
    for (int j = 0; j < Math.min(nums2.length, k); j++) pq.offer(new int[]{0, j});
    while (k-- > 0 && !pq.isEmpty()) {
        int[] p = pq.poll();
        res.add(Arrays.asList(nums1[p[0]], nums2[p[1]]));
        if (p[0] + 1 < nums1.length) pq.offer(new int[]{p[0] + 1, p[1]});
    }
    return res;
}
```

**複雜度：** 時間 O(k log k) · 空間 O(k)
