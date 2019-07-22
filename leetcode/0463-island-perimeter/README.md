## Question

https://leetcode.com/problems/island-perimeter/

## Solutions

```go
func islandPerimeter(grid [][]int) int {
	if len(grid) == 0 {
		return 0
	}

	r, c := len(grid), len(grid[0])

	land, conn := 0, 0
	for i := 0; i < r; i++ {
		for j := 0; j < c; j++ {
			if grid[i][j] == 1 {
				land++
				// check up
				if i > 0 && grid[i-1][j] == 1 {
					conn++
				}
				// check right
				if j < c-1 && grid[i][j+1] == 1 {
					conn++
				}
				// check down
				if i < r-1 && grid[i+1][j] == 1 {
					conn++
				}
				// check left
				if j > 0 && grid[i][j-1] == 1 {
					conn++
				}
			}
		}
	}

	return land*4 - conn
}
```
