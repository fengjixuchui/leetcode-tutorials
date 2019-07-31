## Question

https://leetcode.com/problems/unique-paths-ii/

## Solutions

```go
func uniquePathsWithObstacles(obstacleGrid [][]int) int {
	// m column
	// n row
	m, n := len(obstacleGrid[0]), len(obstacleGrid)

	d := make([][]int, n)

	for row := 0; row < len(d); row++ {
		d[row] = make([]int, m)
	}

	if obstacleGrid[0][0] == 1 {
		return 0
	}
	d[0][0] = 1

	for col := 1; col < m; col++ {
		if obstacleGrid[0][col] == 1 {
			d[0][col] = 0
		} else {
			d[0][col] = d[0][col-1]
		}
	}

	for row := 1; row < n; row++ {
		if obstacleGrid[row][0] == 1 {
			d[row][0] = 0
		} else {
			d[row][0] = d[row-1][0]
		}
	}

	for row := 1; row < n; row++ {
		for col := 1; col < m; col++ {
			if obstacleGrid[row][col] == 1 {
				d[row][col] = 0
			} else {
				d[row][col] = d[row-1][col] + d[row][col-1]
			}
		}
	}

	return d[n-1][m-1]
}
```
