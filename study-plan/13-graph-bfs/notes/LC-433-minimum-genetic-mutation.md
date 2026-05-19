# LC 433 · Minimum Genetic Mutation

| 項目 | 內容 |
|------|------|
| Pattern | BFS |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Minimum Genetic Mutation](https://leetcode.com/problems/minimum-genetic-mutation/) |

**題意：** 基因 start→end，每次改一個字母且中間必須在 bank 內，求最少步數。

**核心：** BFS 最短步：從 start 出發，嘗試 8 字母 × 每位置 3 種替換；在 bank 且未訪問則入隊。

```java
public int minMutation(String startGene, String endGene, String[] bank) {
    Set<String> bankSet = new HashSet<>(Arrays.asList(bank));
    if (!bankSet.contains(endGene)) return -1;
    char[] genes = {'A', 'C', 'G', 'T'};
    Queue<String> q = new ArrayDeque<>();
    Set<String> seen = new HashSet<>();
    q.offer(startGene);
    seen.add(startGene);
    int steps = 0;
    while (!q.isEmpty()) {
        int size = q.size();
        for (int i = 0; i < size; i++) {
            String cur = q.poll();
            if (cur.equals(endGene)) return steps;
            char[] arr = cur.toCharArray();
            for (int j = 0; j < arr.length; j++) {
                char old = arr[j];
                for (char g : genes) {
                    if (g == old) continue;
                    arr[j] = g;
                    String next = new String(arr);
                    if (bankSet.contains(next) && seen.add(next))
                        q.offer(next);
                }
                arr[j] = old;
            }
        }
        steps++;
    }
    return -1;
}
```

**複雜度：** O(N·L·4) 時間（N=bank 大小，L=8），O(N) 空間。
