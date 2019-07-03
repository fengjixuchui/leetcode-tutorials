## Question

https://leetcode.com/problems/set-matrix-zeroes/

## Solutions

```go
func setZeroes(matrix [][]int)  {
    m, n := len(matrix), len(matrix[0])

    rows := make([]bool, m)
    cols := make([]bool, n)

    for i := 0; i < m; i++ {
        for j := 0; j < n; j++ {
            if matrix[i][j] == 0 {
                rows[i] = true
                cols[j] = true
            }
        }
    }

    for i := 0; i < m; i++ {
        for j := 0; j < n; j++ {
            if rows[i] || cols[j] {
                matrix[i][j] = 0
            }
        }
    }
}
```