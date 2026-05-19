# LC 13 · Roman to Integer

| 項目 | 內容 |
|------|------|
| Pattern | String scan |
| 難度 | Easy |
| 狀態 | **done** |
| 題目 | [Roman to Integer](https://leetcode.com/problems/roman-to-integer/) |

**題意：** 羅馬數字轉整數。

**核心：** 左到右；若 **curr < next** 則減 curr 否則加 curr。

```java
public int romanToInt(String s) {
  Map<Character, Integer> m = Map.of(
      'I',1,'V',5,'X',10,'L',50,'C',100,'D',500,'M',1000);
  int ans = 0;
  for (int i = 0; i < s.length(); i++) {
    int curr = m.get(s.charAt(i));
    if (i + 1 < s.length() && curr < m.get(s.charAt(i + 1))) ans -= curr;
    else ans += curr;
  }
  return ans;
}
```

**複雜度：** 時間 O(n) · 空間 O(1)
