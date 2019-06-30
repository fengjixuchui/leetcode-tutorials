## Question

https://leetcode.com/problems/search-a-2d-matrix-ii/

## Solutions

```go
func searchMatrix(matrix [][]int, target int) bool {
    if len(matrix) == 0 {
        return false
    }

    m, n := len(matrix), len(matrix[0])

    i, j := 0, n - 1

    for i < m && j >= 0 {
        if matrix[i][j] > target {
            j--
        } else if matrix[i][j] < target {
            i++
        } else {
            return true
        }
    }

    return false
}
```
