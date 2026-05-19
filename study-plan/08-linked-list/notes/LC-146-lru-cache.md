# LC 146 · LRU Cache

| 項目 | 內容 |
|------|------|
| Pattern | Hash + doubly linked list |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [LRU Cache](https://leetcode.com/problems/lru-cache/) |

**題意：** 實作 LRU Cache：get/put O(1)，容量滿時淘汰最久未用。

**核心：** **HashMap + 雙向鏈結串列**（或 LinkedHashMap accessOrder）。

```java
class LRUCache {
    class Node { int k, v; Node prev, next; Node(int k, int v) { this.k = k; this.v = v; } }
    private final Map<Integer, Node> map = new HashMap<>();
    private final Node head = new Node(0, 0), tail = new Node(0, 0);
    private final int cap;
    public LRUCache(int capacity) {
        cap = capacity;
        head.next = tail; tail.prev = head;
    }
    public int get(int key) {
        if (!map.containsKey(key)) return -1;
        Node n = map.get(key);
        remove(n); insert(n);
        return n.v;
    }
    public void put(int key, int value) {
        if (map.containsKey(key)) { map.get(key).v = value; get(key); return; }
        Node n = new Node(key, value);
        map.put(key, n); insert(n);
        if (map.size() > cap) {
            Node lru = head.next;
            remove(lru);
            map.remove(lru.k);
        }
    }
    private void remove(Node n) { n.prev.next = n.next; n.next.prev = n.prev; }
    private void insert(Node n) { n.prev = tail.prev; n.next = tail; tail.prev.next = n; tail.prev = n; }
}
```

**複雜度：** get/put O(1) · 空間 O(capacity)
