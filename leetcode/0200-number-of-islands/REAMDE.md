## Question

https://leetcode.com/problems/number-of-islands/

## Solutions

```go
// O(m*n) time | O(1) space
func numIslands(grid [][]byte) int {
	if grid == nil || len(grid) == 0 {
		return 0
	}

	row, col, count := len(grid), len(grid[0]), 0

	for i := 0; i < row; i++ {
		for j := 0; j < col; j++ {
			if grid[i][j] == '0' {
				continue
			}
			count++
			dfs(grid, i, j)
		}
	}

	return count
}

func dfs(grid [][]byte, i int, j int) {
	if i < 0 || i >= len(grid) || j < 0 || j >= len(grid[0]) || grid[i][j] == '0' {
		return
	}
	grid[i][j] = '0'
	dfs(grid, i-1, j)
	dfs(grid, i+1, j)
	dfs(grid, i, j+1)
	dfs(grid, i, j-1)
}
```
