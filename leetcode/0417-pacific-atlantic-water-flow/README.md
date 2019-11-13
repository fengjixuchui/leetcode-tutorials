## Question

https://leetcode.com/problems/pacific-atlantic-water-flow/

## Solutions

```go
// Time: O(m*n), Space: O(m*n)
func pacificAtlantic(matrix [][]int) [][]int {
	res := [][]int{}
	if matrix == nil || len(matrix) == 0 || len(matrix[0]) == 0 {
		return res
	}

	n, m := len(matrix), len(matrix[0])
	pacific := make([][]bool, n)
	for row := 0; row < n; row++ {
		pacific[row] = make([]bool, m)
	}
	atlantic := make([][]bool, n)
	for row := 0; row < n; row++ {
		atlantic[row] = make([]bool, m)
	}

	for col := 0; col < m; col++ {
		dfs(matrix, pacific, math.MinInt32, 0, col)
		dfs(matrix, atlantic, math.MinInt32, n-1, col)
	}
	for row := 0; row < n; row++ {
		dfs(matrix, pacific, math.MinInt32, row, 0)
		dfs(matrix, atlantic, math.MinInt32, row, m-1)
	}

	for row := 0; row < n; row++ {
		for col := 0; col < m; col++ {
			if pacific[row][col] && atlantic[row][col] {
				res = append(res, []int{row, col})
			}
		}
	}

	return res
}

func dfs(matrix [][]int, visited [][]bool, height int, row int, col int) {
	n, m := len(matrix), len(matrix[0])

	if (row < 0 || row >= n) || (col < 0 || col >= m || visited[row][col] || matrix[row][col] < height) {
		return
	}

	visited[row][col] = true

	dfs(matrix, visited, matrix[row][col], row-1, col)
	dfs(matrix, visited, matrix[row][col], row, col+1)
	dfs(matrix, visited, matrix[row][col], row+1, col)
	dfs(matrix, visited, matrix[row][col], row, col-1)
}
```

## Tutorials

- https://www.youtube.com/watch?v=5pMmAJWlUMI
