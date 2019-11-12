## Question

https://leetcode.com/problems/unique-paths/

## Solutions

```go
// O(m*n) time | O(m*n) space
func uniquePaths(rows int, cols int) int {
	// 1. Build the record table.
	records := make([][]int, rows)
	for row := 0; row < rows; row++ {
		records[row] = make([]int, cols)
	}

	// Left column will always be 1.
	for row := 0; row < rows; row++ {
		records[row][0] = 1
	}
	// Top row will always be 1.
	for col := 0; col < cols; col++ {
		records[0][col] = 1
	}

	for row := 1; row < rows; row++ {
		for col := 1; col < cols; col++ {
			records[row][col] = records[row-1][col] + records[row][col-1]
		}
	}

	return records[rows-1][cols-1]
}
```
