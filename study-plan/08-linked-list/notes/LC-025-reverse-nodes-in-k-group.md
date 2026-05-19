# LC 25 · Reverse Nodes in k-Group

| 項目 | 內容 |
|------|------|
| Pattern | Reverse k-group |
| 難度 | Hard |
| 狀態 | **done** |
| 題目 | [Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/) |

**題意：** 每 k 個節點一組反轉鏈結串列。

**核心：** 檢查剩餘長度≥k；**反轉 k 個**後遞迴/迭代接下一組。

```java
public ListNode reverseKGroup(ListNode head, int k) {
    ListNode cur = head;
    int count = 0;
    while (cur != null && count < k) { cur = cur.next; count++; }
    if (count < k) return head;
    cur = reverseKGroup(cur, k);
    while (count-- > 0) {
        ListNode nxt = head.next;
        head.next = cur;
        cur = head;
        head = nxt;
    }
    return cur;
}
```

**複雜度：** 時間 O(n) · 空間 O(n/k) 遞迴
