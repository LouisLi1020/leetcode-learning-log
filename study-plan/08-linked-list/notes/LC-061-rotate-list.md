# LC 61 · Rotate List

| 項目 | 內容 |
|------|------|
| Pattern | Find tail + connect |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Rotate List](https://leetcode.com/problems/rotate-list/) |

**題意：** 將鏈結串列向右旋轉 k 次。

**核心：** 成環：找尾接頭，斷在 **n-k%n** 處，新頭為斷點後。

```java
public ListNode rotateRight(ListNode head, int k) {
    if (head == null || head.next == null) return head;
    int n = 1;
    ListNode tail = head;
    while (tail.next != null) { tail = tail.next; n++; }
    k %= n;
    if (k == 0) return head;
    tail.next = head;
    for (int i = 0; i < n - k; i++) tail = tail.next;
    ListNode newHead = tail.next;
    tail.next = null;
    return newHead;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
