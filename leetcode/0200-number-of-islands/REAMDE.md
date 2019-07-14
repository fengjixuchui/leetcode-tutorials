## Question

https://leetcode.com/problems/number-of-islands/

## Solutions

```go
func dfs(grid [][]byte, visit [][]bool, i, j int) {
	r, c := len(grid), len(grid[0])
	if i < 0 || i >= r || j < 0 || j >= c || grid[i][j] == '0' || visit[i][j] {
		return
	}
	visit[i][j] = true
	dfs(grid, visit, i-1, j)
	dfs(grid, visit, i+1, j)
	dfs(grid, visit, i, j-1)
	dfs(grid, visit, i, j+1)
}

func numIslands(grid [][]byte) int {
	if grid == nil || len(grid) == 0 {
		return 0
	}

	r, c := len(grid), len(grid[0])
	visit := make([][]bool, r)
	for i := 0; i < r; i++ {
		visit[i] = make([]bool, c)
	}
	count := 0

	for i := 0; i < r; i++ {
		for j := 0; j < c; j++ {
			if grid[i][j] == '0' || visit[i][j] {
				continue
			}
			count++
			dfs(grid, visit, i, j)
		}
	}

	return count
}
```
