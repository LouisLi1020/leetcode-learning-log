# LC 238 · Product of Array Except Self

| 項目 | 內容 |
|------|------|
| 難度 | Medium |
| Pattern | Prefix/suffix product |
| 狀態 | **partial** |
| 題目 | [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/) |

## 預期要點

- 不能用除法（含零時）
- `answer[i] = (左側乘積) × (右側乘積)`
- O(n) 時間、O(1) 額外空間（輸出不計）
