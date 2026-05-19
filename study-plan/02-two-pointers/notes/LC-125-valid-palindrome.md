# LC 125 · Valid Palindrome

| 項目 | 內容 |
|------|------|
| Pattern | Two pointers |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/) |

**題意：** 判斷字串是否為回文（只考慮英數，忽略大小寫）。

**核心：** 雙指標 **l/r** 跳過非英數，比較 toLowerCase。

```java
public boolean isPalindrome(String s) {
    int l = 0, r = s.length() - 1;
    while (l < r) {
        while (l < r && !Character.isLetterOrDigit(s.charAt(l))) l++;
        while (l < r && !Character.isLetterOrDigit(s.charAt(r))) r--;
        if (Character.toLowerCase(s.charAt(l)) != Character.toLowerCase(s.charAt(r))) return false;
        l++; r--;
    }
    return true;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
