## Question

https://leetcode.com/problems/unique-paths/

## Solutions

```go
func uniquePaths(m int, n int) int {
	if m < 1 || n < 1 {
		return 0
	}
	records := make([][]int, m)
	for i := range records {
		records[i] = make([]int, n)
	}

	for row := 0; row < m; row++ {
		records[row][0] = 1
	}
	for col := 0; col < n; col++ {
		records[0][col] = 1
	}

	for row := 1; row < m; row++ {
		for col := 1; col < n; col++ {
			records[row][col] = records[row-1][col] + records[row][col-1]
		}
	}

	return records[m-1][n-1]
}
```
