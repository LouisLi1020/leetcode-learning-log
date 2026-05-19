# LC 141 · Linked List Cycle

| 項目 | 內容 |
|------|------|
| Pattern | Floyd |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/) |

**題意：** 鏈結串列是否有環。

**核心：** **Floyd 快慢指標**：快指標走兩步、慢走一步，相遇即有環。

```java
public boolean hasCycle(ListNode head) {
    ListNode slow = head, fast = head;
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
        if (slow == fast) return true;
    }
    return false;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
