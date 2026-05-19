# LC 295 · Find Median from Data Stream

| 項目 | 內容 |
|------|------|
| Pattern | Two heaps |
| 難度 | Hard |
| 狀態 | **done** |
| 題目 | [Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/) |

**題意：** 資料流動態中位數。

**核心：** **大根堆** 存較小一半、**小根堆** 存較大一半；保持 `maxHeap.size() >= minHeap.size()` 且差 ≤1。

| 堆 | 角色 |
|------|------|
| maxHeap | 下半部（較小） |
| minHeap | 上半部（較大） |

```java
class MedianFinder {
    PriorityQueue<Integer> lo = new PriorityQueue<>(Collections.reverseOrder());
    PriorityQueue<Integer> hi = new PriorityQueue<>();
    public void addNum(int num) {
        lo.offer(num);
        hi.offer(lo.poll());
        if (lo.size() < hi.size()) lo.offer(hi.poll());
    }
    public double findMedian() {
        return lo.size() > hi.size() ? lo.peek() : (lo.peek() + hi.peek()) / 2.0;
    }
}
```

**複雜度：** addNum O(log n) · findMedian O(1)
