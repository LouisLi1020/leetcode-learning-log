# LC 92 · Reverse Linked List II

| 項目 | 內容 |
|------|------|
| Pattern | Reverse segment |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Reverse Linked List II](https://leetcode.com/problems/reverse-linked-list-ii/) |

**題意：** 反轉鏈結串列位置 left 到 right（1-indexed）。

**核心：** dummy + 走至 left 前，**反轉 k 個節點**（頭插或迭代反轉）。

```java
public ListNode reverseBetween(ListNode head, int left, int right) {
    ListNode dummy = new ListNode(0, head), pre = dummy;
    for (int i = 0; i < left - 1; i++) pre = pre.next;
    ListNode cur = pre.next;
    for (int i = 0; i < right - left; i++) {
        ListNode nxt = cur.next;
        cur.next = nxt.next;
        nxt.next = pre.next;
        pre.next = nxt;
    }
    return dummy.next;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
