# LC 67 · Add Binary

| 項目 | 內容 |
|------|------|
| Pattern | Bit / simulation |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Add Binary](https://leetcode.com/problems/add-binary/) |

**題意：** 二進位字串相加。

**核心：** 由尾往前模擬進位 `carry`；結果反轉。

```java
public String addBinary(String a, String b) {
    StringBuilder sb = new StringBuilder();
    int i = a.length() - 1, j = b.length() - 1, carry = 0;
    while (i >= 0 || j >= 0 || carry > 0) {
        int sum = carry;
        if (i >= 0) sum += a.charAt(i--) - '0';
        if (j >= 0) sum += b.charAt(j--) - '0';
        sb.append(sum % 2);
        carry = sum / 2;
    }
    return sb.reverse().toString();
}
```

**複雜度：** 時間 O(max(m,n)) · 空間 O(1)（不含輸出）
