## Question

https://leetcode.com/problems/search-a-2d-matrix/

## Solutions

```go
func searchMatrix(matrix [][]int, target int) bool {
	if len(matrix) == 0 || len(matrix[0]) == 0 {
		return false
	}

	// get the rows count and column count
	r, c := len(matrix), len(matrix[0])
	l, r := 0, r*c-1

	for l <= r {
		m := l + (r-l)/2
		curRow, curCol := m/c, m%c

		if matrix[curRow][curCol] < target {
			l = m + 1
		} else if matrix[curRow][curCol] > target {
			r = m - 1
		} else {
			return true
		}
	}

	return false
}
```
