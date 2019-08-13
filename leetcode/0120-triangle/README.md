## Question

https://leetcode.com/problems/triangle/

## Solutions

```go
func minimumTotal(triangle [][]int) int {
	rows := len(triangle)
	if triangle == nil {
		return 0
	}

	for row := 0; row < rows; row++ {
		for col := 0; col < len(triangle[row]); col++ {
			if row == 0 && col == 0 {
				continue
			}

			if col == 0 {
				triangle[row][col] += triangle[row-1][col]
			} else if row == col {
				triangle[row][col] += triangle[row-1][col-1]
			} else {
				triangle[row][col] += Min(triangle[row-1][col-1], triangle[row-1][col])
			}

		}
	}

	min := math.MaxInt32
	lastRow := rows - 1
	for i := 0; i < len(triangle[lastRow]); i++ {
		min = Min(triangle[lastRow][i], min)
	}

	return min
}

func Min(a, b int) int {
	if a > b {
		return b
	}
	return a
}
```
