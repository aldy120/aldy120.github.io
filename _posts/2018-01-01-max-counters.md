# MaxCounters
A cool kata in codility lesson. [Here](https://codility.com/demo/take-sample-test/max_counters/) is the link.

# Description
給你一個 array A 長度為 M，範圍在 [1, N + 1] 中，要你根據這個 array 的順序做出相對應的操作。

你有 N 個 counters 一開始都設為 0。

如果今天 `A[i]` 在 [1, N] 區間中，就把 `A[i]` 的 counter 加一。其中 i 在 [1, M] 之間。

如果今天 `A[i]` 是 N + 1，那所有 counters 裡面的直都換成 目前 counters 中最多的那個的目前數字。

最後輸出 counters。

# Trivial Solution
對於每個 `A[i]`:
- 如果 `A[i] <= N`，將該 counter 加一。
- 如果 `A[i] === N + 1` ，找出目前 counters 中最大值，並把 counters 全部設為該值。

Time complexity: O(MN)
Space complexity: O(N)

# Time: O(M+N) As Hint
若能簡化原先演算法要做多次的"把 counters 全部設為該值"變成只做一次，就能解決。

記錄每次遇到 N+1 前的最大值，並把他們都累加起來，直到最後要輸出時再把他們加到每個元素中。

```js
function solution(N, A) {
    // write your code in JavaScript (Node.js 6.4.0)
    var count = []
    var max = 0
    var maxSum = 0
    var M = A.length
    // spilt the array by which element equal N + 1
    for (var i = 0; i < M; i++) {
        if (A[i] <= N) {
            // (A[i] - 1) be the final index in output counters
            count[A[i] - 1] = count[A[i] - 1] + 1 || 1
            max = Math.max(max, count[A[i] - 1])
        } else {
            maxSum += max
            max = 0
            count = []
        }
    }
    
    return Array(N).fill(maxSum).map((x, i) => x + (count[i] || 0))
}
```