## Question

https://leetcode.com/problems/search-a-2d-matrix-ii/

## Solutions

```go
func searchMatrix(matrix [][]int, target int) bool {
	if matrix == nil || len(matrix) == 0 {
		return false
	}

	m, n := len(matrix), len(matrix[0])
	row, col := 0, n-1

	for row < m && col >= 0 {
		if matrix[row][col] == target {
			return true
		}

		if matrix[row][col] < target {
			row++
		} else {
			col--
		}
	}

	return false
}
```
