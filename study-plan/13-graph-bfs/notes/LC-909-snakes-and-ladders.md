# LC 909 · Snakes and Ladders

| 項目 | 內容 |
|------|------|
| Pattern | BFS |
| 難度 | Medium |
| 狀態 | **done** |
| 題目 | [Snakes and Ladders](https://leetcode.com/problems/snakes-and-ladders/) |

**題意：** 10×10 蛇梯棋：從 1 到 n² 最少步數（骰子 1–6）。

**核心：** BFS 按「格數」擴展：每步試 1–6，BFS 座標轉 board 行列；遇蛇/梯直接傳送。

```java
public int snakesAndLadders(int[][] board) {
    int n = board.length, target = n * n;
    boolean[] seen = new boolean[target + 1];
    Queue<Integer> q = new ArrayDeque<>();
    q.offer(1);
    seen[1] = true;
    int steps = 0;
    while (!q.isEmpty()) {
        int size = q.size();
        for (int i = 0; i < size; i++) {
            int sq = q.poll();
            if (sq == target) return steps;
            for (int d = 1; d <= 6 && sq + d <= target; d++) {
                int next = sq + d;
                int[] rc = toRC(next, n);
                if (board[rc[0]][rc[1]] != -1) next = board[rc[0]][rc[1]];
                if (!seen[next]) { seen[next] = true; q.offer(next); }
            }
        }
        steps++;
    }
    return -1;
}
int[] toRC(int sq, int n) {
    int r = (sq - 1) / n, c = (sq - 1) % n;
    if (r % 2 == 1) c = n - 1 - c;
    return new int[]{n - 1 - r, c};
}
```

**複雜度：** O(n²) 時間，O(n²) 空間。
