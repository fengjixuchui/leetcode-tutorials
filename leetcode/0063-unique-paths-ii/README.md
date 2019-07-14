## Question

https://leetcode.com/problems/unique-paths-ii/

## Solutions

```go
func uniquePathsWithObstacles(g [][]int) int {
	row, col := len(g), len(g[0])
	d := make([][]int, row)
	for r := 0; r < row; r++ {
		d[r] = make([]int, col)
	}

	if g[0][0] == 1 {
		d[0][0] = 0
	} else {
		d[0][0] = 1
	}

	for r := 1; r < row; r++ {
		if g[r][0] == 1 {
			d[r][0] = 0
		} else {
			d[r][0] = d[r-1][0]
		}
	}

	for c := 1; c < col; c++ {
		if g[0][c] == 1 {
			d[0][c] = 0
		} else {
			d[0][c] = d[0][c-1]
		}
	}

	for r := 1; r < row; r++ {
		for c := 1; c < col; c++ {
			if g[r][c] == 1 {
				d[r][c] = 0
			} else {
				d[r][c] = d[r-1][c] + d[r][c-1]
			}
		}
	}

	return d[row-1][col-1]
}
```
