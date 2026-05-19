# LC 68 · Text Justification

| 項目 | 內容 |
|------|------|
| Pattern | Simulation |
| 難度 | Hard |
| 狀態 | **done** |
| 題目 | [Text Justification](https://leetcode.com/problems/text-justification/) |

**題意：** 將單字陣列排版成 maxWidth 寬，每行左右對齊（最後一行左對齊）。

**核心：** 貪心湊行：盡量多放單字；非末行用 **空格均分**（多餘空格放左側）。

```java
public List<String> fullJustify(String[] words, int maxWidth) {
    List<String> res = new ArrayList<>();
    int i = 0;
    while (i < words.length) {
        int j = i, lineLen = 0;
        while (j < words.length && lineLen + words[j].length() + (j - i) <= maxWidth) {
            lineLen += words[j++].length();
        }
        int gaps = j - i - 1;
        StringBuilder line = new StringBuilder();
        if (j == words.length || gaps == 0) {
            for (int k = i; k < j; k++) {
                line.append(words[k]);
                if (k < j - 1) line.append(' ');
            }
            while (line.length() < maxWidth) line.append(' ');
        } else {
            int spaces = maxWidth - lineLen;
            int spaceEach = spaces / gaps, extra = spaces % gaps;
            for (int k = i; k < j - 1; k++) {
                line.append(words[k]);
                for (int s = 0; s < spaceEach + (k - i < extra ? 1 : 0); s++)
                    line.append(' ');
            }
            line.append(words[j - 1]);
        }
        res.add(line.toString());
        i = j;
    }
    return res;
}
```

**複雜度：** 時間 O(n·L) · 空間 O(輸出)
