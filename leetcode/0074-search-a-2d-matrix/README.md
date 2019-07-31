## Question

https://leetcode.com/problems/search-a-2d-matrix/

## Solutions

```go
func searchMatrix(matrix [][]int, target int) bool {
	if matrix == nil || len(matrix) == 0 {
		return false
	}

	// m rows
	// n columns
	m, n := len(matrix), len(matrix[0])

	l, r := 0, m*n-1

	for l <= r {
		m := l + (r-l)/2
		row, col := m/n, m%n

		if matrix[row][col] == target {
			return true
		}

		if matrix[row][col] < target {
			l = m + 1
		} else {
			r = m - 1
		}
	}

	return false
}
```
