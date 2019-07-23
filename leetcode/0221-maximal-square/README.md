## Question

https://leetcode.com/problems/maximal-square/

## Solutions

```go
func maximalSquare(matrix [][]byte) int {
	// Handle edge cases.
	if len(matrix) == 0 {
		return 0
	}

	m, n := len(matrix), len(matrix[0])

	// Build the cache.
	d := make([][]int, m)
	for i := 0; i < m; i++ {
		d[i] = make([]int, n)
	}

	ans := 0
	for i := 0; i < m; i++ {
		for j := 0; j < n; j++ {
			d[i][j] = int(matrix[i][j] - '0')

			if d[i][j] == 0 {
				continue
			}

			if i == 0 || j == 0 {
				// If it's top row or left column remain as it is.
			} else {
				d[i][j] = Min(d[i-1][j-1], Min(d[i-1][j], d[i][j-1])) + 1
			}

			ans = Max(ans, d[i][j]*d[i][j])
		}
	}

	return ans
}

func Max(a, b int) int {
	if a > b {
		return a
	}
	return b
}

func Min(a, b int) int {
	if a > b {
		return b
	}
	return a
}
```
