# LC 12 · Integer to Roman

| 項目 | 內容 |
|------|------|
| Pattern | Greedy subtract |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Integer to Roman](https://leetcode.com/problems/integer-to-roman/) |

**題意：** 整數轉羅馬數字（1–3999）。

**核心：** 由大到小貪心：值-符號表，while num>=val 拼接並減去。

```java
public String intToRoman(int num) {
    int[] vals = {1000,900,500,400,100,90,50,40,10,9,5,4,1};
    String[] syms = {"M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"};
    StringBuilder sb = new StringBuilder();
    for (int i = 0; i < vals.length; i++) {
        while (num >= vals[i]) { sb.append(syms[i]); num -= vals[i]; }
    }
    return sb.toString();
}
```

**複雜度：** 時間 O(1) · 空間 O(1)
