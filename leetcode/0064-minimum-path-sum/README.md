## Question

https://leetcode.com/problems/minimum-path-sum/

## Solutions

```go
func minPathSum(grid [][]int) int {
	if grid == nil {
		return 0
	}

	m, n := len(grid), len(grid[0])

	minSum := make([][]int, m)
	for i := 0; i < len(minSum); i++ {
		minSum[i] = make([]int, n)
	}

	minSum[0][0] = grid[0][0]

	for row := 1; row < m; row++ {
		minSum[row][0] = minSum[row-1][0] + grid[row][0]
	}
	for col := 1; col < n; col++ {
		minSum[0][col] = minSum[0][col-1] + grid[0][col]
	}

	for row := 1; row < m; row++ {
		for col := 1; col < n; col++ {
			minSum[row][col] = Min(minSum[row-1][col], minSum[row][col-1]) + grid[row][col]
		}
	}

	return minSum[m-1][n-1]
}

func Min(a, b int) int {
	if a > b {
		return b
	}
	return a
}
```
