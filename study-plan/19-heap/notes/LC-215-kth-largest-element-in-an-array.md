# LC 215 · Kth Largest Element in an Array

| 項目 | 內容 |
|------|------|
| Pattern | Heap / quickselect |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/) |

**題意：** 找陣列第 k 大元素。

**核心：** **最小堆** 維持 k 個最大；或 **quickselect** 平均 O(n)。

```java
public int findKthLargest(int[] nums, int k) {
    PriorityQueue<Integer> minHeap = new PriorityQueue<>();
    for (int x : nums) {
        minHeap.offer(x);
        if (minHeap.size() > k) minHeap.poll();
    }
    return minHeap.peek();
}
```

**複雜度：** 時間 O(n log k) · 空間 O(k)
