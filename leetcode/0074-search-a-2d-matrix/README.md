## Question

https://leetcode.com/problems/search-a-2d-matrix/

## Solutions

```go
func searchMatrix(matrix [][]int, target int) bool {
	if matrix == nil || len(matrix) == 0 {
		return false
	}

	m, n := len(matrix), len(matrix[0])
	low, high := 0, m*n-1

	for low <= high {
		mid := low + (high-low)/2
		r, c := mid/n, mid%n
		if matrix[r][c] == target {
			return true
		} else if matrix[r][c] > target {
			high = mid - 1
		} else {
			low = mid + 1
		}
	}

	return false
}
```
