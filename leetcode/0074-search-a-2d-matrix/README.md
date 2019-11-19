## Question

https://leetcode.com/problems/search-a-2d-matrix/

## Solutions

```go
// Time: O(logn), Space: O(1)
func searchMatrix(matrix [][]int, target int) bool {
	if matrix == nil || len(matrix) == 0 || len(matrix[0]) == 0 {
		return false
	}

	m, n := len(matrix), len(matrix[0])

	left, right := 0, m*n-1

	for left <= right {
		mid := left + (right-left)/2
		row, col := mid/n, mid%n
		if matrix[row][col] > target {
			right = mid - 1
		} else if matrix[row][col] < target {
			left = mid + 1
		} else {
			return true
		}
	}

	return false
}

```
